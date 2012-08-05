--- 
layout: post 
title: Migrating MongoDB between cloud-based providers 
--- 

[GitWatcher](http://gitwatcher.com/) is an experimental platform currently
based on Rails 3.1.3 and MongoDB/[Mongoid](http://mongoid.org/), one of the
most promising pairs of Object-Document-Mapper for NoSQL DBs, in the Ruby
landscape.

While the backend is on a cloud, the frontend is on another. Infact, the Rails
app is running on Heroku Celadon Cedar Stack and the DB was initially running
on [MongoHQ](https://mongohq.com/home), a cloud-based hosted database solution
for [MongoDB](http://www.mongodb.org/).

Although that was fine at the beginning when only a few data were collected,
free plan with 16MB of storage, can quickly become a shortage while you still
need to go on testing, maintaining low cost of exercise at the same time but,
magic of cloud computing competition, we can have a free plan for up to 240MB
also.

[Heroku](http://www.heroku.com/) Platform as a Service (PaaS), provide many
add-ons to easily plug in external services like
[MongLab](https://mongolab.com/home) for example, which currently have a free
plan 15 times greater than MongoHQ, to go on testing for free with MongoDB.

So here we go, migrating between clouds should never be easier, let me show
you.

First we add Heroku addons to our application. You can do it either through
the  web console  or through the command line interface ( see [managing-add-
ons](http://devcenter.heroku.com/articles/managing-add-ons) for more details )
:

    
    $ # ADD HEROKU ADDONS:  
    $ heroku addons:add mongolab:starter

than we query Heroku config to get MongoHQ connection user and password for
current application :

    
    $ # QUERY HEROKU CONFIG:  
    $ heroku config --long | grep MONGOHQ_URL   
    MONGOHQ_URL => mongodb://<user>:<password>@staff.mongohq.com:10075/app1707530

now we dump MongoDB from MongoHQ :

    
    $ # DUMP MongoHQ DB:  
    $ mongodump -h staff.mongohq.com:10075 -d app1707530 -u user -p password     
    connected to: staff.mongohq.com:10075  
    DATABASE: app1707530     to     dump/app1707530  
            app1707530.system.users to dump/app1707530/system.users.bson  
                     1 objects  
            app1707530.system.indexes to dump/app1707530/system.indexes.bson  
                     2 objects  
            app1707530.users to dump/app1707530/users.bson  
                     2 objects  
    ...

and we restore the DB on MongoLab, after extracting user and password the same
way we did before :

    
    $ # RESTORE ON MongoLab:  
    $ mongorestore -h ds029257.mongolab.com:29257 -d gitwatcher-db -u user -p password ./dump/app1707530  
    connected to: ds029257.mongolab.com:29257  
    Wed Jan 11 23:05:17 ./dump/app1707530/users.bson  
    Wed Jan 11 23:05:17      going into namespace [gitwatcher-db.users]  
    Wed Jan 11 23:05:24      2 objects found  
    Wed Jan 11 23:05:24 ./dump/app1707530/system.users.bson  
    Wed Jan 11 23:05:24      going into namespace [gitwatcher-db.system.users]  
    Wed Jan 11 23:05:24      1 objects found  
    Wed Jan 11 23:05:24 ./dump/app1707530/system.indexes.bson  
    Wed Jan 11 23:05:24      going into namespace [gitwatcher-db.system.indexes]  
    Wed Jan 11 23:05:24      2 objects found  
    ...

last, change production configuration in config/mongoid.yml, which should look
like the following :

    
    production:
    
     uri: <%= ENV['MONGOLAB_URI'] %>  
    
    

just remain to commit and push back to Heroku.

Done in 10 minutes.

We did it online but, if you are under heavy DB load, is better to disable
access to your application for some length of time.

You can use Heroku’s built in
[maintenance](https://devcenter.heroku.com/articles/maintenance-mode) mode. It
will serve a static page to all visitors, while still allowing you to run rake
tasks or console commands.

It's great isn't it ? Let me know what you think about.

