--- 
layout: post 
title: GitWatcher is built on top of several amazing Ruby Gems 
--- 

I'd like to thanks one by one all the developers who contributed directly or
undirectly to the amazing edge we are living in Ruby domain.

Here it is a dump of Ruby Gems which GitWatcher is currently built on top of.

My personal special thanks goes to [MongoID](http://mongoid.org/) project and
in special way to [durran _(Durran Jordan)_](https://github.com/durran).

Without his support [GitWatcher](http://gitwatcher.com/) would have never been
started.

    GIT
    
      remote: [https://github.com/mongoid/mongoid.git](https://github.com/mongoid/
    mongoid.git)
    
      revision: 512b7107ea79721c1780890eff8eec663f381bf2
    
      specs:
    
        mongoid (3.0.0)
    
          activemodel (~> 3.1)
    
          mongo (~> 1.3)
    
          tzinfo (~> 0.3.22)
    
    
    
    GEM
    
      remote: [http://rubygems.org/](http://rubygems.org/)
    
      specs:
    
        ZenTest (4.6.2)
    
        actionmailer (3.2.2)
    
          actionpack (= 3.2.2)
    
          mail (~> 2.4.0)
    
        actionpack (3.2.2)
    
          activemodel (= 3.2.2)
    
          activesupport (= 3.2.2)
    
          builder (~> 3.0.0)
    
          erubis (~> 2.7.0)
    
          journey (~> 1.0.1)
    
          rack (~> 1.4.0)
    
          rack-cache (~> 1.1)
    
          rack-test (~> 0.6.1)
    
          sprockets (~> 2.1.2)
    
        activemodel (3.2.2)
    
          activesupport (= 3.2.2)
    
          builder (~> 3.0.0)
    
        activerecord (3.2.2)
    
          activemodel (= 3.2.2)
    
          activesupport (= 3.2.2)
    
          arel (~> 3.0.2)
    
          tzinfo (~> 0.3.29)
    
        activeresource (3.2.2)
    
          activemodel (= 3.2.2)
    
          activesupport (= 3.2.2)
    
        activesupport (3.2.2)
    
          i18n (~> 0.6)
    
          multi_json (~> 1.0)
    
        addressable (2.2.7)
    
        archive-tar-minitar (0.5.2)
    
        arel (3.0.2)
    
        autotest-notification (2.3.4)
    
          autotest-standalone (~> 4.5)
    
        autotest-rails (4.1.2)
    
          ZenTest (~> 4.5)
    
        autotest-standalone (4.5.9)
    
        bson (1.6.1)
    
        bson_ext (1.6.1)
    
          bson (~> 1.6.1)
    
        builder (3.0.0)
    
        capybara (1.1.2)
    
          mime-types (>= 1.16)
    
          nokogiri (>= 1.3.3)
    
          rack (>= 1.0.0)
    
          rack-test (>= 0.5.4)
    
          selenium-webdriver (~> 2.0)
    
          xpath (~> 0.1.4)
    
        childprocess (0.3.1)
    
          ffi (~> 1.0.6)
    
        chronic (0.6.7)
    
        coffee-rails (3.2.2)
    
          coffee-script (>= 2.2.0)
    
          railties (~> 3.2.0)
    
        coffee-script (2.2.0)
    
          coffee-script-source
    
          execjs
    
        coffee-script-source (1.2.0)
    
        columnize (0.3.6)
    
        commonjs (0.2.0)
    
          therubyracer (~> 0.9.9)
    
        cucumber (1.1.9)
    
          builder (>= 2.1.2)
    
          diff-lcs (>= 1.1.2)
    
          gherkin (~> 2.9.0)
    
          json (>= 1.4.6)
    
          term-ansicolor (>= 1.0.6)
    
        cucumber-rails (1.3.0)
    
          capybara (>= 1.1.2)
    
          cucumber (>= 1.1.8)
    
          nokogiri (>= 1.5.0)
    
        daemons (1.0.10)
    
        dalli (1.1.5)
    
        database_cleaner (0.7.1)
    
        diff-lcs (1.1.3)
    
        em-websocket (0.3.6)
    
          addressable (>= 2.1.1)
    
          eventmachine (>= 0.12.9)
    
        erubis (2.7.0)
    
        eventmachine (0.12.10)
    
        execjs (1.3.0)
    
          multi_json (~> 1.0)
    
        factory_girl (2.6.3)
    
          activesupport (>= 2.3.9)
    
        factory_girl_rails (1.7.0)
    
          factory_girl (~> 2.6.0)
    
          railties (>= 3.0.0)
    
        faraday (0.7.6)
    
          addressable (~> 2.2)
    
          multipart-post (~> 1.1)
    
          rack (~> 1.1)
    
        faraday-stack (0.1.5)
    
          faraday (>= 0.6, < 0.8)
    
        ffi (1.0.11)
    
        gem_plugin (0.2.3)
    
        gherkin (2.9.0)
    
          json (>= 1.4.6)
    
        git (1.2.5)
    
        google_visualr (2.1.2)
    
        guard (1.0.1)
    
          ffi (>= 0.5.0)
    
          thor (~> 0.14.6)
    
        guard-bundler (0.1.3)
    
          bundler (>= 1.0.0)
    
          guard (>= 0.2.2)
    
        guard-cucumber (0.7.5)
    
          cucumber (>= 0.10)
    
          guard (>= 0.8.3)
    
        guard-livereload (0.4.2)
    
          em-websocket (>= 0.2.0)
    
          guard (>= 0.10.0)
    
          multi_json (~> 1.0)
    
        guard-rails (0.1.0)
    
          guard (>= 0.2.2)
    
        guard-rspec (0.6.0)
    
          guard (>= 0.10.0)
    
        guard-spork (0.5.2)
    
          guard (>= 0.10.0)
    
          spork (>= 0.8.4)
    
        haml (3.1.4)
    
        haml-rails (0.3.4)
    
          actionpack (~> 3.0)
    
          activesupport (~> 3.0)
    
          haml (~> 3.0)
    
          railties (~> 3.0)
    
        hashie (1.2.0)
    
        hike (1.2.1)
    
        httparty (0.8.1)
    
          multi_json
    
          multi_xml
    
        i18n (0.6.0)
    
        jar_wrapper (0.1.2)
    
          jeweler
    
          jeweler
    
          zip
    
          zip
    
        jeweler (1.8.3)
    
          bundler (~> 1.0)
    
          git (>= 1.2.5)
    
          rake
    
          rdoc
    
        journey (1.0.3)
    
        jquery-rails (2.0.1)
    
          railties (>= 3.2.0, < 5.0)
    
          thor (~> 0.14)
    
        json (1.6.5)
    
        kaminari (0.13.0)
    
          actionpack (>= 3.0.0)
    
          activesupport (>= 3.0.0)
    
          railties (>= 3.0.0)
    
        launchy (2.0.5)
    
          addressable (~> 2.2.6)
    
        less (2.0.10)
    
          commonjs (~> 0.2.0)
    
          therubyracer (~> 0.9.9)
    
        less-rails (2.1.7)
    
          actionpack (>= 3.1)
    
          less (~> 2.0.7)
    
        libnotify (0.7.2)
    
        libv8 (3.3.10.4)
    
        linecache19 (0.5.12)
    
          ruby_core_source (>= 0.1.4)
    
        mail (2.4.3)
    
          i18n (>= 0.4.0)
    
          mime-types (~> 1.16)
    
          treetop (~> 1.4.8)
    
        meta-tags (1.2.6)
    
          actionpack
    
        mime-types (1.17.2)
    
        mongo (1.6.1)
    
          bson (~> 1.6.1)
    
        mongoid_taggable_with_context (0.8.0)
    
          mongoid (>= 2.0.0)
    
        mongrel (1.2.0.pre2)
    
          daemons (~> 1.0.10)
    
          gem_plugin (~> 0.2.3)
    
        multi_json (1.1.0)
    
        multi_xml (0.4.1)
    
        multipart-post (1.1.5)
    
        nokogiri (1.5.2)
    
        oauth2 (0.5.2)
    
          faraday (~> 0.7)
    
          multi_json (~> 1.0)
    
        omniauth (1.0.3)
    
          hashie (~> 1.2)
    
          rack
    
        omniauth-github (1.0.1)
    
          omniauth (~> 1.0)
    
          omniauth-oauth2 (~> 1.0)
    
        omniauth-oauth2 (1.0.0)
    
          oauth2 (~> 0.5.0)
    
          omniauth (~> 1.0)
    
        pg (0.13.2)
    
        polyglot (0.3.3)
    
        progstr-ruby (1.0.6)
    
          multi_json
    
        rack (1.4.1)
    
        rack-cache (1.2)
    
          rack (>= 0.4)
    
        rack-ssl (1.3.2)
    
          rack
    
        rack-test (0.6.1)
    
          rack (>= 1.0)
    
        rails (3.2.2)
    
          actionmailer (= 3.2.2)
    
          actionpack (= 3.2.2)
    
          activerecord (= 3.2.2)
    
          activeresource (= 3.2.2)
    
          activesupport (= 3.2.2)
    
          bundler (~> 1.0)
    
          railties (= 3.2.2)
    
        railties (3.2.2)
    
          actionpack (= 3.2.2)
    
          activesupport (= 3.2.2)
    
          rack-ssl (~> 1.3.2)
    
          rake (>= 0.8.7)
    
          rdoc (~> 3.4)
    
          thor (~> 0.14.6)
    
        rake (0.9.2.2)
    
        rb-inotify (0.8.8)
    
          ffi (>= 0.5.0)
    
        rdoc (3.12)
    
          json (~> 1.4)
    
        rspec (2.8.0)
    
          rspec-core (~> 2.8.0)
    
          rspec-expectations (~> 2.8.0)
    
          rspec-mocks (~> 2.8.0)
    
        rspec-core (2.8.0)
    
        rspec-expectations (2.8.0)
    
          diff-lcs (~> 1.1.2)
    
        rspec-mocks (2.8.0)
    
        rspec-rails (2.8.1)
    
          actionpack (>= 3.0)
    
          activesupport (>= 3.0)
    
          railties (>= 3.0)
    
          rspec (~> 2.8.0)
    
        ruby-debug-base19 (0.11.25)
    
          columnize (>= 0.3.1)
    
          linecache19 (>= 0.5.11)
    
          ruby_core_source (>= 0.1.4)
    
        ruby-debug19 (0.11.6)
    
          columnize (>= 0.3.1)
    
          linecache19 (>= 0.5.11)
    
          ruby-debug-base19 (>= 0.11.19)
    
        ruby_core_source (0.1.5)
    
          archive-tar-minitar (>= 0.5.2)
    
        rubyzip (0.9.6.1)
    
        sass (3.1.15)
    
        sass-rails (3.2.4)
    
          railties (~> 3.2.0)
    
          sass (>= 3.1.10)
    
          tilt (~> 1.3)
    
        search_magic (0.3.0)
    
          chronic
    
          mongoid (>= 2.4.3)
    
        selenium (0.2.5)
    
          jar_wrapper
    
          jeweler
    
        selenium-client (1.2.18)
    
        selenium-webdriver (2.20.0)
    
          childprocess (>= 0.2.5)
    
          ffi (~> 1.0)
    
          multi_json (~> 1.0)
    
          rubyzip
    
        spork (0.9.0)
    
        sprockets (2.1.2)
    
          hike (~> 1.2)
    
          rack (~> 1.0)
    
          tilt (~> 1.1, != 1.3.0)
    
        sqlite3 (1.3.5)
    
        stathat (0.0.3)
    
        systemu (2.4.2)
    
        term-ansicolor (1.0.7)
    
        therubyracer (0.9.10)
    
          libv8 (~> 3.3.10)
    
        thin (1.3.1)
    
          daemons (>= 1.0.9)
    
          eventmachine (>= 0.12.6)
    
          rack (>= 1.0.0)
    
        thor (0.14.6)
    
        tilt (1.3.3)
    
        treetop (1.4.10)
    
          polyglot
    
          polyglot (>= 0.3.1)
    
        twitter-bootstrap-rails (2.0.1)
    
          actionpack (>= 3.1)
    
          less-rails (~> 2.1.5)
    
          railties (>= 3.1)
    
        tzinfo (0.3.32)
    
        uglifier (1.2.3)
    
          execjs (>= 0.3.0)
    
          multi_json (>= 1.0.2)
    
        xpath (0.1.4)
    
          nokogiri (~> 1.3)
    
        zip (2.0.2)
    
    
    PLATFORMS
    
      ruby
    
    
    DEPENDENCIES
    
      ZenTest
    
      autotest-notification
    
      autotest-rails
    
      bson
    
      bson_ext
    
      builder
    
      capybara
    
      coffee-rails
    
      cucumber
    
      cucumber-rails
    
      dalli
    
      database_cleaner
    
      factory_girl_rails
    
      faraday-stack
    
      google_visualr
    
      guard-bundler
    
      guard-cucumber
    
      guard-livereload
    
      guard-rails
    
      guard-rspec
    
      guard-spork
    
      haml
    
      haml-rails
    
      httparty
    
      jquery-rails
    
      kaminari
    
      launchy
    
      libnotify
    
      meta-tags
    
      mongo
    
      mongoid!
    
      mongoid_taggable_with_context (= 0.8.0)
    
      mongrel (= 1.2.0.pre2)
    
      omniauth
    
      omniauth-github
    
      pg
    
      progstr-ruby
    
      rack
    
      rails (= 3.2.2)
    
      rake
    
      rb-inotify
    
      rspec-rails
    
      ruby-debug19
    
      sass-rails
    
      search_magic
    
      selenium
    
      selenium-client
    
      selenium-webdriver
    
      sqlite3
    
      stathat
    
      systemu
    
      therubyracer
    
      thin
    
      twitter-bootstrap-rails (~> 2.0.1.0)
    
      uglifier
    
