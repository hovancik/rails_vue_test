1. init docker stuff
2. `docker-compose build`

```
db uses an image, skipping
Building web
Step 1/10 : FROM ruby:2.4.2
 ---> c7715c1eb8fe
Step 2/10 : RUN apt-get update -qq && apt-get install -y build-essential libpq-dev
 ---> Using cache
 ---> dd98cbc6515f
Step 3/10 : RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - && apt-get install -y nodejs
 ---> Using cache
 ---> 117cec297f13
Step 4/10 : RUN apt-get update && apt-get install -y curl apt-transport-https wget && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && apt-get update && apt-get install -y yarn
 ---> Using cache
 ---> 0dbae0255e3d
Step 5/10 : RUN mkdir /rails_vue_test
 ---> Running in e0eb01da9048
 ---> c08325f040ca
Removing intermediate container e0eb01da9048
Step 6/10 : WORKDIR /rails_vue_test
 ---> a276d9cffa7a
Removing intermediate container 648cac99d7ab
Step 7/10 : ADD Gemfile /rails_vue_test/Gemfile
 ---> aced6bea2214
Step 8/10 : ADD Gemfile.lock /rails_vue_test/Gemfile.lock
 ---> 832395688773
Step 9/10 : RUN bundle install
 ---> Running in aa0bc3be25dd
Fetching gem metadata from https://rubygems.org/..........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies...
Fetching rake 12.2.1
Installing rake 12.2.1
Fetching concurrent-ruby 1.0.5
Installing concurrent-ruby 1.0.5
Fetching i18n 0.9.1
Installing i18n 0.9.1
Fetching minitest 5.10.3
Installing minitest 5.10.3
Fetching thread_safe 0.3.6
Installing thread_safe 0.3.6
Fetching tzinfo 1.2.4
Installing tzinfo 1.2.4
Fetching activesupport 5.1.4
Installing activesupport 5.1.4
Fetching builder 3.2.3
Installing builder 3.2.3
Fetching erubi 1.7.0
Installing erubi 1.7.0
Fetching mini_portile2 2.3.0
Installing mini_portile2 2.3.0
Fetching nokogiri 1.8.1
Installing nokogiri 1.8.1 with native extensions
Fetching rails-dom-testing 2.0.3
Installing rails-dom-testing 2.0.3
Fetching crass 1.0.2
Installing crass 1.0.2
Fetching loofah 2.1.1
Installing loofah 2.1.1
Fetching rails-html-sanitizer 1.0.3
Installing rails-html-sanitizer 1.0.3
Fetching actionview 5.1.4
Installing actionview 5.1.4
Fetching rack 2.0.3
Installing rack 2.0.3
Fetching rack-test 0.7.0
Installing rack-test 0.7.0
Fetching actionpack 5.1.4
Installing actionpack 5.1.4
Fetching nio4r 2.1.0
Installing nio4r 2.1.0 with native extensions
Fetching websocket-extensions 0.1.2
Installing websocket-extensions 0.1.2
Fetching websocket-driver 0.6.5
Installing websocket-driver 0.6.5 with native extensions
Fetching actioncable 5.1.4
Installing actioncable 5.1.4
Fetching globalid 0.4.1
Installing globalid 0.4.1
Fetching activejob 5.1.4
Installing activejob 5.1.4
Fetching mini_mime 1.0.0
Installing mini_mime 1.0.0
Fetching mail 2.7.0
Installing mail 2.7.0
Fetching actionmailer 5.1.4
Installing actionmailer 5.1.4
Fetching activemodel 5.1.4
Installing activemodel 5.1.4
Fetching arel 8.0.0
Installing arel 8.0.0
Fetching activerecord 5.1.4
Installing activerecord 5.1.4
Using bundler 1.16.0
Fetching method_source 0.9.0
Installing method_source 0.9.0
Fetching thor 0.20.0
Installing thor 0.20.0
Fetching railties 5.1.4
Installing railties 5.1.4
Fetching sprockets 3.7.1
Installing sprockets 3.7.1
Fetching sprockets-rails 3.2.1
Installing sprockets-rails 3.2.1
Fetching rails 5.1.4
Installing rails 5.1.4
Bundle complete! 1 Gemfile dependency, 38 gems now installed.
Bundled gems are installed into `/usr/local/bundle`
 ---> 3869ffaba0a7
Removing intermediate container aa0bc3be25dd
Step 10/10 : ADD . /rails_vue_test
 ---> 36ab6b96a105
Successfully built 36ab6b96a105
Successfully tagged railsvuetest_web:latest
```
