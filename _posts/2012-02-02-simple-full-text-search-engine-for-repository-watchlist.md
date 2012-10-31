--- 
layout: post 
title: Simple full-text search engine for repository watchlist 
--- 

Many of you have been asking for this since the beginning. Today, I have the
pleasure to announce that full-text search engine for your repository
watchlist, is finally here.


People who are watching several hundred of GitHub repositories like me, after
login the first time, get a big list of untagged git projects and starting
tagging could be a bit tricky.


Even if you can reorder your pages sorting by fields, ‘By Tag’ tab in your
dasboard is still empty and you may have several pages to go through, that’s
way a search engine became essential.

There are many open source full-text search engines like
[elasticsearch](http://www.elasticsearch.org/) and
[sphinx](http://sphinxsearch.com/) with relative Ruby API and DSL  like
[Tire](http://karmi.github.com/tire/) /
[Mebla](https://github.com/cousine/mebla) and[mongoid-
sphinx](https://github.com/redbeard-tech/mongoid-sphinx), but we have two
constraints here:

  1. a mongoid [embedded one to many](http://mongoid.org/docs/relations/embedded/1-n.html) model on Rails 3.1 to search full text
  2. deploy on heroku without having to pay for add-ons, initially

All heroku Full-Text Search add-ons currently, seem to have just paying plans
which are not good to start with, see [Flying
Sphinx](http://addons.heroku.com/flying_sphinx) and
[Websolr](http://addons.heroku.com/websolr).

There is also [Searchify IndexTank](http://addons.heroku.com/searchify) but is
currently Beta, then for our pourpose we decided to go even simpler using
[search_magic](https://github.com/joshuabowers/search_magic) gem.

We tried [mongoid_search](https://github.com/mauriciozaffari/mongoid_search)
and [mongoid_fulltext](https://github.com/aaw/mongoid_fulltext) too, but we
have not been able to make them working with mongoid [embedded one to
many](http://mongoid.org/docs/relations/embedded/1-n.html).

That said, the search is very simple and restrictive : you insert a set of
words and it match a permutation of the exact terms only, case unsensitive,
looking full-text into "repo", "description" and "tags" fields  of each
repository, which means that in my case, searching for_ "authentication
omniath" _will find the following five responces :


![](http://gitwatcher.com/blog/img/full_text_search.png)


but searching for _"rack __authentication omniath"_  gets back  just one
responce, as you can see :


![](http://gitwatcher.com/blog/img/full_text_search_result.png)


Very simple, but is what we need at the moment. Any feedback is welcome.

