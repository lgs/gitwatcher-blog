--- 
layout: post 
title: Easy and cooperative project categorization is now open to GitWatcher users
--- 

As announced in [the previous
article](http://blog.gitwatcher.com/post/22589388119/a-semi-automatic-
categorization-of-github-projects), categorization system is now open to
GitWatcher users. Adding Categories is now possible by [Sign in with
Github](http://gitwatcher.com/auth/github) then going to [categories
page](http://gitwatcher.com/categories). You’ll find a list of categories
already in place and a form where you can add your own.


![](https://lh3.googleusercontent.com/THY2EJOfMljmIwjzfDI_InbYTzVb_pbx_9U8I-
Yuw62Wv1N0fR2VXilHkVCkCau2zU0BYSvGiy0OJkGfI9xMm2utmKyYVanlw4vP3w4PjWl7BLxnkJQ)


Suppose you are interested in the emerging web presentation model “[Model View
ViewModel (MVVM)](http://en.wikipedia.org/wiki/Model_View_ViewModel)” and you
want to know which projects and libraries on [GitHub](http://github.com/) are
implementing that design pattern and how popular, mature and maintained they
are. You just need a quick view of what is going on in the market before you
dig into the code, right ?


Well just go to the trends page and click to [Javascript MVC/MVVM
Frameworks](http://gitwatcher.com/trends) and you’ll see a list of trending
projects extracted from how GitWatcher users have already tagged their own
watched repositories, with at last three tags: javascript - mvc - framework.


![](https://lh4.googleusercontent.com/68joG4d0-SaEx5OPXNYSXmc9LLGh3DOVMwqDuyyW
LdFHi48tTgFiKdq1Wnet48eVvaeY3oJsARe0C974To1pwR_feZWj5kQJzXGjZMlGO_ngPgiFuoc)


That is just a category I made for myself to stay on top of that field but you
can now make your own, just [add category field and one or more
tags](http://gitwatcher.com/categories) which are going to be the minimum
matches for GitWatcher extractor engine to assign a repository to your new
category.


Categories will be public, each user will see them, just try to follow some
few conventions :


- Categories should be most of all plural, even if not necessarily, like fore example “Content Management Systems”, “Ruby Web Frameworks”, “Mongodb Clients” and so on.  
- Tags should be singular. When composed, like in “api-client “ or  “api-builder”, minus ("-") char should be used to join two words.   

GitWatcher, will probably put in place some automatic normalization,
aggregation or correction filters but until now, let's see how will it work
the easiest way. Of course any suggestion are welcome.


Please let me know what do you think about and how would you do that, post
your comment or shoot your tweet @gitwatcher, your contribution is welcome.

_**UPDATE Sat Jun 2 :**_

_To populate a new created category, at last one repository on
[GitWatcher](http://gitwatcher.com/) has to be tagged with the minimum tag set
you added for that category. If nobody has a repository tagged that way,
you’ll end up with an empty category which will be removed automatically in
few hours. To evoid that go to your watchlist by [Sign in with Github
](http://gitwatcher.com/auth/github)and just tag a repo with the tags you just
added, otherwise leave it empty and it will be cleared up automatically._

