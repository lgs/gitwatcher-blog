---
layout: post
title: Tumblr to Jekyll Blog Migration
---
After half an year of blogging on tumblr GitWatcher’s blog has now decided to go for [Blogging Like a Hacker](http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html) well known way, by jekylling on rails.  

There is really no reason to delegate third-level domain for blogging ( blog.gitwatcher.com vs [gitwatcher.com/blog](http://gitwatcher.com/blog) ) losing SEO and ranking, [having less control and reliability on our blog content.](http://webapps.stackexchange.com/questions/22586/my-tumblr-blog-disappeared), eventually.

[Jekyll](http://jekyllrb.com/) is an open-source blog-aware static site generator and [Rails](http://rubyonrails.org/) as you know, is the “main” application engine behind [gitwatcher.com](http://gitwatcher.com) ( but no longer the only one, more on future articles ).

Mounting a Jekyll blog on Rails, can be done manually several different ways, but if you want to go easy peasy, you really have to see this article about [bloggy](http://www.engineyard.com/blog/2012/introducing-bloggy-a-simple-way-to-add-a-jekyll-blog-to-any-rails-application/) gem.

[Bloggy](https://github.com/zbruhnke/bloggy) makes it easy to run a Jekyll blog right within your existing Rails application with no changes to your current configuration. It helps you generate a jekyll blog by using rails generator commands similar to the ones you are used to already.

Blog’s layout, is done by glorious front-end framework [twitter bootstrap](http://twitter.github.com/bootstrap/) ( impressive ~40k stars and 10k forks on [https://github.com/twitter/bootstrap](https://github.com/twitter/bootstrap) ), now provided via CDN by [BootstrapCDN](http://www.bootstrapcdn.com/), and perfectly integrated with the rest of the site, that’s cool.

Data migration has been smooth, thanks to [Blog Migration Tutorial](https://github.com/mojombo/jekyll/wiki/Blog-Migrations). You can find Tumblr procedure at the end of the page, but you can find migration scripts and procedures for WordPress, Drupal, Movable Type, Typo 4+, TextPattern, Mephisto, Blogger (Blogspot), Posterous, as well.

Then once again, no reason to go outsourcing. That’s all for this post, I would like to know what do you think about, please feel free to share your experience by adding comments.
