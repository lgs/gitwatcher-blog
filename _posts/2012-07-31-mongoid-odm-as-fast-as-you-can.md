--- 
layout: post 
title: MongoID ODM as fast as you can 
--- 


In the [previous article](http://gitwatcher.com/blog/easy-and-cooperative-project-categorization-is-now-open-to-gitwatcher-users.html), 
we announced our first attempt of croudsourcing repository categorization on GitWatcher platform.


Based on hybrid model, [gitwatcher
categories](http://gitwatcher.com/categories) are automatically extracted by a
collector, which simply list them based on the tags they have been associated
to by each user.


A new category can be added by a logged in gitwatcher, who gives it a name and
a set of tags to be associated with. If another user tags a repository with
the same tag set, that repo will be displayed into the list, after being
collected ( which currently happen once a day ).


Now, part of the the collector code, was looking like the following at first :


    Competitor  = Struct.new(:html_url, :description, :user)
    competitors = []
    User.all.map do |user|
      user.watchlists.all.map do |wl|
        if wl.tags_array == ["ruby", "web", "framework"]
           competitors « Competitor.new(wl.html_url, wl.description, wl.user.nickname)
       end
     end
    end

    

and a semplified underline datamodel was similar to the following:  
      
     

    class User
      include Mongoid::Document
      field :nickname
      embeds_many :watchlists
    end
    
    class Watchlist
      include Mongoid::Document
      field :html_url
      field :description
      field :tags_array, type: Array
      embedded_in :user
    end



Well, that was great at first, but the data was growing and the entire
operation became time and CPU consuming. I start googling around, looking for
better, more efficient and effective way to use the amazing[ mongoid
ODM](http://mongoid.org/) driver.


An interesting response came from a post I made on
[stackoverflow.com](http://stackoverflow.com/questions/10121977/extracting-modelling-and-changing-data-model-with-mongoid-mongodb) where I was suggested
to consider the following enhancements ( thanks goes to
[rubish](http://stackoverflow.com/users/479167/rubish) ) :

  * Filter the users with db query instead of filtering in application
  * only fetch fields you need from db, rather than the whole user objects


the code example was posted on the same answer. Here it is :



    Competitor = Struct.new(:html_url, :description, :user)
    competitors = []
    User.where('watchlists.tags_array' => %w[ruby web framework]).only(:nickname, :watchlists).each do |u|
      u.watchlists.where(:tags_array => %w[ruby web framework]).each do |wl|
        competitors « Competitor.new(wl.html_url, wl.description, u.nickname)
      end
    end



I Took the time to get some measures … and surprise,  it results really faster
and less cpu consuming:


first code :
    1.9.2p290 :157 > Competitor  = Struct.new(:html_url, :description, :user)
    1.9.2p290 :158 > competitors = []
    => []
    
    1.9.2p290 :159 > Benchmark.bm(10) do |x|
    1.9.2p290 :160 >     x.report("first:") do
    1.9.2p290 :161 >       User.all.map do |user|
    1.9.2p290 :162 >           user.watchlists.all.map do |wl|
    1.9.2p290 :163 >               if wl.tags_array == ["ruby", "web",
    "framework"]
    1.9.2p290 :164?>                   competitors « Competitor.new(wl.html_url, wl.description, wl.user.nickname)
    1.9.2p290 :165?>               end
    1.9.2p290 :166?>           end
    1.9.2p290 :167?>       end
    1.9.2p290 :168?>     end
    1.9.2p290 :169?>   x.report("second:") do
    1.9.2p290 :170 >       User.all.map do |user|
    1.9.2p290 :171 >           user.watchlists.all.map do |wl|
    1.9.2p290 :172 >               if wl.tags_array == ["ruby", "web", "framework"]
    1.9.2p290 :173?>                   competitors « Competitor.new(wl.html_url, wl.description, wl.user.nickname)
    1.9.2p290 :174?>               end
    1.9.2p290 :175?>           end
    1.9.2p290 :176?>       end
    1.9.2p290 :177?>     end
    1.9.2p290 :178?>   x.report("third:") do
    1.9.2p290 :179 >       User.all.map do |user|
    1.9.2p290 :180 >           user.watchlists.all.map do |wl|
    1.9.2p290 :181 >               if wl.tags_array == ["ruby", "web", "framework"]
    1.9.2p290 :182?>                   competitors « Competitor.new(wl.html_url, wl.description, wl.user.nickname)
    1.9.2p290 :183?>               end
    1.9.2p290 :184?>           end
    1.9.2p290 :185?>       end
    1.9.2p290 :186?>     end
    1.9.2p290 :187?>   end
    
                   user     system      total        real
    
    first:    MONGODB (30ms) heroku_app1707530['users'].find({})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 6320857008182747446
    
    MONGODB [DEBUG] cursor.refresh() for cursor 6320857008182747446
    
     1.460000   0.010000   1.470000 (  1.475545)
    
    second:   MONGODB (24ms) heroku_app1707530['users'].find({})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 8580701579081246457
    
    MONGODB [DEBUG] cursor.refresh() for cursor 8580701579081246457
    
     1.470000   0.010000   1.480000 (  1.494812)
    
    third:    MONGODB (24ms) heroku_app1707530['users'].find({})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 6472818135140756688
    
    MONGODB [DEBUG] cursor.refresh() for cursor 6472818135140756688
    
     1.490000   0.010000   1.500000 (  1.505000)
    
    => true
    
    1.9.2p290 :188 >



vs. second code :

    1.9.2p290 :065 > Competitor  = Struct.new(:html_url, :description, :user)
    1.9.2p290 :066 > competitors = []
    => []
    1.9.2p290 :067 > Benchmark.bm(10) do |x|
    1.9.2p290 :068 >     x.report("first:") {User.where('watchlists.tags_array' => %w[ruby web framework]).only(:nickname, :watchlists).each{|u|u.watchlists.where(:tags_array => %w[ruby web framework]).each{|wl|competitors « Competitor.new(wl.html_url, wl.description, u.nickname)}}}
    
    1.9.2p290 :069?>   x.report("second:") {User.where('watchlists.tags_array' => %w[ruby web framework]).only(:nickname, :watchlists).each{|u|u.watchlists.where(:tags_array => %w[ruby web framework]).each{|wl|competitors « Competitor.new(wl.html_url, wl.description, u.nickname)}}}
    
    1.9.2p290 :070?>   x.report("third:") {User.where('watchlists.tags_array' => %w[ruby web framework]).only(:nickname, :watchlists).each{|u|u.watchlists.where(:tags_array => %w[ruby web framework]).each{|wl|competitors « Competitor.new(wl.html_url, wl.description, u.nickname)}}}
    1.9.2p290 :071?>   end
    
                   user     system      total        real
    
    first:    MONGODB (163ms)
    heroku_app1707530['users'].find({"watchlists.tags_array"=>["ruby", "web",
    "framework"]}, {:_type=>1, :nickname=>1, :watchlists=>1})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 7239021952645827000
    
     0.330000   0.000000   0.330000 (  0.380199)
    
    second:   MONGODB (164ms)
    heroku_app1707530['users'].find({"watchlists.tags_array"=>["ruby", "web",
    "framework"]}, {:_type=>1, :nickname=>1, :watchlists=>1})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 4816095738351422260
    
     0.320000   0.010000   0.330000 (  0.381196)
    
    third:    MONGODB (125ms)
    heroku_app1707530['users'].find({"watchlists.tags_array"=>["ruby", "web",
    "framework"]}, {:_type=>1, :nickname=>1, :watchlists=>1})
    
    MONGODB [DEBUG] cursor.refresh() for cursor 5014359782446173361
    
     0.390000   0.010000   0.400000 (  0.397241)
    
    => true
    
    1.9.2p290 :072 >


As you can see the speed up is quite impressive. MongoID/MongoDB is a defacto
NoSQL tech for data crunching and big data in Ruby


[ ![mongodb, riack, couchdb, elasticsearch, cassandra Job Trends graph](http://www.indeed.com/trendgraph/jobgraph.png?q=mongodb%2C+riack%2C+couchdb%2C+elasticsearch%2C+cassandra)](http://www.indeed.com/jobtrends?q=mongodb%2C+riack%2C+couchdb%2C+elasticsearch%2C+cassandra)


… but it takes some mind shift to be fully understood and utilized.


I hope it can help,

feel free to add your comments and experiences.

