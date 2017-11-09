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

3. `docker-compose run web rails new . --force --database=postgresql --webpack=vue --skip-coffee --skip-turbolinks --skip-action-cable`

```
Creating network "railsvuetest_default" with the default driver
Creating railsvuetest_db_1 ...
Creating railsvuetest_db_1 ... done
       exist
       force  README.md
      create  Rakefile
      create  config.ru
      create  .gitignore
       force  Gemfile
         run  git init from "."
Reinitialized existing Git repository in /rails_vue_test/.git/
      create  app
      create  app/assets/config/manifest.js
      create  app/assets/javascripts/application.js
      create  app/assets/javascripts/cable.js
      create  app/assets/stylesheets/application.css
      create  app/channels/application_cable/channel.rb
      create  app/channels/application_cable/connection.rb
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/jobs/application_job.rb
      create  app/mailers/application_mailer.rb
      create  app/models/application_record.rb
      create  app/views/layouts/application.html.erb
      create  app/views/layouts/mailer.html.erb
      create  app/views/layouts/mailer.text.erb
      create  app/assets/images/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      create  bin
      create  bin/bundle
      create  bin/rails
      create  bin/rake
      create  bin/setup
      create  bin/update
      create  bin/yarn
      create  config
      create  config/routes.rb
      create  config/application.rb
      create  config/environment.rb
      create  config/secrets.yml
      create  config/puma.rb
      create  config/spring.rb
      create  config/environments
      create  config/environments/development.rb
      create  config/environments/production.rb
      create  config/environments/test.rb
      create  config/initializers
      create  config/initializers/application_controller_renderer.rb
      create  config/initializers/assets.rb
      create  config/initializers/backtrace_silencers.rb
      create  config/initializers/cookies_serializer.rb
      create  config/initializers/cors.rb
      create  config/initializers/filter_parameter_logging.rb
      create  config/initializers/inflections.rb
      create  config/initializers/mime_types.rb
      create  config/initializers/new_framework_defaults_5_1.rb
      create  config/initializers/wrap_parameters.rb
      create  config/locales
      create  config/locales/en.yml
      create  config/boot.rb
      create  config/database.yml
      create  db
      create  db/seeds.rb
      create  lib
      create  lib/tasks
      create  lib/tasks/.keep
      create  lib/assets
      create  lib/assets/.keep
      create  log
      create  log/.keep
      create  public
      create  public/404.html
      create  public/422.html
      create  public/500.html
      create  public/apple-touch-icon-precomposed.png
      create  public/apple-touch-icon.png
      create  public/favicon.ico
      create  public/robots.txt
      create  test/fixtures
      create  test/fixtures/.keep
      create  test/fixtures/files
      create  test/fixtures/files/.keep
      create  test/controllers
      create  test/controllers/.keep
      create  test/mailers
      create  test/mailers/.keep
      create  test/models
      create  test/models/.keep
      create  test/helpers
      create  test/helpers/.keep
      create  test/integration
      create  test/integration/.keep
      create  test/test_helper.rb
      create  test/system
      create  test/system/.keep
      create  test/application_system_test_case.rb
      create  tmp
      create  tmp/.keep
      create  tmp/cache
      create  tmp/cache/assets
      create  vendor
      create  vendor/.keep
      create  package.json
      remove  config/cable.yml
      remove  app/assets/javascripts/cable.js
      remove  app/channels
      remove  config/initializers/cors.rb
      remove  config/initializers/new_framework_defaults_5_1.rb
         run  bundle install
Don't run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-root users on this machine.
The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
Fetching gem metadata from https://rubygems.org/.........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies...
Using rake 12.2.1
Using concurrent-ruby 1.0.5
Using i18n 0.9.1
Using minitest 5.10.3
Using thread_safe 0.3.6
Using tzinfo 1.2.4
Using activesupport 5.1.4
Using builder 3.2.3
Using erubi 1.7.0
Using mini_portile2 2.3.0
Using nokogiri 1.8.1
Using rails-dom-testing 2.0.3
Using crass 1.0.2
Using loofah 2.1.1
Using rails-html-sanitizer 1.0.3
Using actionview 5.1.4
Using rack 2.0.3
Using rack-test 0.7.0
Using actionpack 5.1.4
Using nio4r 2.1.0
Using websocket-extensions 0.1.2
Using websocket-driver 0.6.5
Using actioncable 5.1.4
Using globalid 0.4.1
Using activejob 5.1.4
Using mini_mime 1.0.0
Using mail 2.7.0
Using actionmailer 5.1.4
Using activemodel 5.1.4
Using arel 8.0.0
Using activerecord 5.1.4
Fetching public_suffix 3.0.1
Installing public_suffix 3.0.1
Fetching addressable 2.5.2
Installing addressable 2.5.2
Fetching bindex 0.5.0
Installing bindex 0.5.0 with native extensions
Using bundler 1.16.0
Fetching byebug 9.1.0
Installing byebug 9.1.0 with native extensions
Fetching xpath 2.1.0
Installing xpath 2.1.0
Fetching capybara 2.15.4
Installing capybara 2.15.4
Fetching ffi 1.9.18
Installing ffi 1.9.18 with native extensions
Fetching childprocess 0.8.0
Installing childprocess 0.8.0
Fetching execjs 2.7.0
Installing execjs 2.7.0
Fetching multi_json 1.12.2
Installing multi_json 1.12.2
Fetching jbuilder 2.7.0
Installing jbuilder 2.7.0
Fetching rb-fsevent 0.10.2
Installing rb-fsevent 0.10.2
Fetching rb-inotify 0.9.10
Installing rb-inotify 0.9.10
Fetching ruby_dep 1.5.0
Installing ruby_dep 1.5.0
Fetching listen 3.1.5
Installing listen 3.1.5
Using method_source 0.9.0
Fetching pg 0.21.0
Installing pg 0.21.0 with native extensions
Fetching puma 3.10.0
Installing puma 3.10.0 with native extensions
Fetching rack-proxy 0.6.2
Installing rack-proxy 0.6.2
Using thor 0.20.0
Using railties 5.1.4
Using sprockets 3.7.1
Using sprockets-rails 3.2.1
Using rails 5.1.4
Fetching rubyzip 1.2.1
Installing rubyzip 1.2.1
Fetching sass-listen 4.0.0
Installing sass-listen 4.0.0
Fetching sass 3.5.3
Installing sass 3.5.3
Fetching tilt 2.0.8
Installing tilt 2.0.8
Fetching sass-rails 5.0.6
Installing sass-rails 5.0.6
Fetching selenium-webdriver 3.7.0
Installing selenium-webdriver 3.7.0
Fetching spring 2.0.2
Installing spring 2.0.2
Fetching spring-watcher-listen 2.0.1
Installing spring-watcher-listen 2.0.1
Fetching uglifier 3.2.0
Installing uglifier 3.2.0
Fetching web-console 3.5.1
Installing web-console 3.5.1
Fetching webpacker 3.0.2
Installing webpacker 3.0.2
Bundle complete! 15 Gemfile dependencies, 67 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
       rails  webpacker:install
      create  config/webpacker.yml
Copying webpack core config and loaders
      create  config/webpack
      create  config/webpack/development.js
      create  config/webpack/environment.js
      create  config/webpack/production.js
      create  config/webpack/test.js
Copying .postcssrc.yml to app root directory
      create  .postcssrc.yml
Copying .babelrc to app root directory
      create  .babelrc
Creating javascript app source directory
      create  app/javascript
      create  app/javascript/packs/application.js
Installing binstubs
         run  bundle binstubs webpacker from "."
Skipped webpack and webpack-dev-server since they already exist.
If you want to overwrite skipped stubs, use --force.
      append  .gitignore
Installing all JavaScript dependencies
         run  yarn add @rails/webpacker coffeescript@1.12.7 from "."
yarn add v1.3.2
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
info fsevents@1.1.2: The platform "linux" is incompatible with this module.
info "fsevents@1.1.2" is an optional dependency and failed compatibility check. Excluding it from installation.
[3/4] Linking dependencies...
warning "@rails/webpacker > postcss-cssnext@3.0.2" has unmet peer dependency "caniuse-lite@^1.0.30000697".
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 617 new dependencies.
├─ @rails/webpacker@3.0.2
├─ abbrev@1.1.1
├─ acorn-dynamic-import@2.0.2
├─ acorn@5.2.1
├─ adjust-sourcemap-loader@1.1.0
├─ ajv-keywords@2.1.1
├─ ajv@5.3.0
├─ align-text@0.1.4
├─ alphanum-sort@1.0.2
├─ amdefine@1.0.1
├─ ansi-regex@2.1.1
├─ ansi-styles@2.2.1
├─ any-promise@0.1.0
├─ anymatch@1.3.2
├─ aproba@1.2.0
├─ are-we-there-yet@1.1.4
├─ argparse@1.0.9
├─ arr-diff@2.0.0
├─ arr-flatten@1.1.0
├─ array-find-index@1.0.2
├─ array-unique@0.2.1
├─ asn1.js@4.9.2
├─ asn1@0.2.3
├─ assert-plus@1.0.0
├─ assert@1.4.1
├─ async-each@1.0.1
├─ async-foreach@0.1.3
├─ async@2.6.0
├─ asynckit@0.4.0
├─ atob@1.1.3
├─ autoprefixer@7.1.6
├─ aws-sign2@0.7.0
├─ aws4@1.6.0
├─ babel-code-frame@6.26.0
├─ babel-core@6.26.0
├─ babel-generator@6.26.0
├─ babel-helper-builder-binary-assignment-operator-visitor@6.24.1
├─ babel-helper-call-delegate@6.24.1
├─ babel-helper-define-map@6.26.0
├─ babel-helper-explode-assignable-expression@6.24.1
├─ babel-helper-function-name@6.24.1
├─ babel-helper-get-function-arity@6.24.1
├─ babel-helper-hoist-variables@6.24.1
├─ babel-helper-optimise-call-expression@6.24.1
├─ babel-helper-regex@6.26.0
├─ babel-helper-remap-async-to-generator@6.24.1
├─ babel-helper-replace-supers@6.24.1
├─ babel-helpers@6.24.1
├─ babel-loader@7.1.2
├─ babel-messages@6.23.0
├─ babel-plugin-check-es2015-constants@6.22.0
├─ babel-plugin-syntax-async-functions@6.13.0
├─ babel-plugin-syntax-class-properties@6.13.0
├─ babel-plugin-syntax-dynamic-import@6.18.0
├─ babel-plugin-syntax-exponentiation-operator@6.13.0
├─ babel-plugin-syntax-object-rest-spread@6.13.0
├─ babel-plugin-syntax-trailing-function-commas@6.22.0
├─ babel-plugin-transform-async-to-generator@6.24.1
├─ babel-plugin-transform-class-properties@6.24.1
├─ babel-plugin-transform-es2015-arrow-functions@6.22.0
├─ babel-plugin-transform-es2015-block-scoped-functions@6.22.0
├─ babel-plugin-transform-es2015-block-scoping@6.26.0
├─ babel-plugin-transform-es2015-classes@6.24.1
├─ babel-plugin-transform-es2015-computed-properties@6.24.1
├─ babel-plugin-transform-es2015-destructuring@6.23.0
├─ babel-plugin-transform-es2015-duplicate-keys@6.24.1
├─ babel-plugin-transform-es2015-for-of@6.23.0
├─ babel-plugin-transform-es2015-function-name@6.24.1
├─ babel-plugin-transform-es2015-literals@6.22.0
├─ babel-plugin-transform-es2015-modules-amd@6.24.1
├─ babel-plugin-transform-es2015-modules-commonjs@6.26.0
├─ babel-plugin-transform-es2015-modules-systemjs@6.24.1
├─ babel-plugin-transform-es2015-modules-umd@6.24.1
├─ babel-plugin-transform-es2015-object-super@6.24.1
├─ babel-plugin-transform-es2015-parameters@6.24.1
├─ babel-plugin-transform-es2015-shorthand-properties@6.24.1
├─ babel-plugin-transform-es2015-spread@6.22.0
├─ babel-plugin-transform-es2015-sticky-regex@6.24.1
├─ babel-plugin-transform-es2015-template-literals@6.22.0
├─ babel-plugin-transform-es2015-typeof-symbol@6.23.0
├─ babel-plugin-transform-es2015-unicode-regex@6.24.1
├─ babel-plugin-transform-exponentiation-operator@6.24.1
├─ babel-plugin-transform-object-rest-spread@6.26.0
├─ babel-plugin-transform-regenerator@6.26.0
├─ babel-plugin-transform-strict-mode@6.24.1
├─ babel-polyfill@6.26.0
├─ babel-preset-env@1.6.1
├─ babel-register@6.26.0
├─ babel-runtime@6.26.0
├─ babel-template@6.26.0
├─ babel-traverse@6.26.0
├─ babel-types@6.26.0
├─ babylon@6.18.0
├─ balanced-match@0.4.2
├─ base64-js@1.2.1
├─ bcrypt-pbkdf@1.0.1
├─ big.js@3.2.0
├─ binary-extensions@1.10.0
├─ block-stream@0.0.9
├─ bn.js@4.11.8
├─ brace-expansion@1.1.8
├─ braces@1.8.5
├─ brorand@1.1.0
├─ browserify-aes@1.1.1
├─ browserify-cipher@1.0.0
├─ browserify-des@1.0.0
├─ browserify-rsa@4.0.1
├─ browserify-sign@4.0.4
├─ browserify-zlib@0.1.4
├─ browserslist@2.8.0
├─ buffer-xor@1.0.3
├─ buffer@4.9.1
├─ builtin-modules@1.1.1
├─ builtin-status-codes@3.0.0
├─ camelcase-keys@2.1.0
├─ camelcase@4.1.0
├─ caniuse-api@2.0.0
├─ caniuse-db@1.0.30000760
├─ caniuse-lite@1.0.30000760
├─ caseless@0.12.0
├─ center-align@0.1.3
├─ chalk@1.1.3
├─ chokidar@1.7.0
├─ cipher-base@1.0.4
├─ clap@1.2.3
├─ cliui@3.2.0
├─ clone-deep@0.3.0
├─ clone@1.0.3
├─ co@4.6.0
├─ coa@1.0.4
├─ code-point-at@1.1.0
├─ coffee-loader@0.8.0
├─ coffeescript@1.12.7
├─ color-convert@1.9.1
├─ color-name@1.1.3
├─ color-string@1.5.2
├─ color@1.0.3
├─ colormin@1.1.2
├─ colors@1.1.2
├─ combined-stream@1.0.5
├─ commondir@1.0.1
├─ complex.js@2.0.4
├─ compression-webpack-plugin@1.0.1
├─ concat-map@0.0.1
├─ console-browserify@1.1.0
├─ console-control-strings@1.1.0
├─ constants-browserify@1.0.0
├─ convert-source-map@1.5.0
├─ core-js@2.5.1
├─ core-util-is@1.0.2
├─ cosmiconfig@2.2.2
├─ create-ecdh@4.0.0
├─ create-hash@1.1.3
├─ create-hmac@1.1.6
├─ cross-spawn@3.0.1
├─ crypto-browserify@3.12.0
├─ css-color-function@1.3.3
├─ css-color-names@0.0.4
├─ css-loader@0.28.7
├─ css-selector-tokenizer@0.7.0
├─ css-unit-converter@1.1.1
├─ css@2.2.1
├─ cssesc@0.1.0
├─ cssnano@3.10.0
├─ csso@2.3.2
├─ currently-unhandled@0.4.1
├─ d@1.0.0
├─ dashdash@1.14.1
├─ date-now@0.1.4
├─ debug@2.6.9
├─ decamelize@1.2.0
├─ decimal.js@7.2.3
├─ defined@1.0.0
├─ delayed-stream@1.0.0
├─ delegates@1.0.0
├─ des.js@1.0.0
├─ detect-indent@4.0.0
├─ diffie-hellman@5.0.2
├─ domain-browser@1.1.7
├─ ecc-jsbn@0.1.1
├─ electron-to-chromium@1.3.27
├─ elliptic@6.4.0
├─ emojis-list@2.1.0
├─ enhanced-resolve@3.4.1
├─ errno@0.1.4
├─ error-ex@1.3.1
├─ es5-ext@0.10.35
├─ es6-iterator@2.0.3
├─ es6-map@0.1.5
├─ es6-set@0.1.5
├─ es6-symbol@3.1.1
├─ es6-weak-map@2.0.2
├─ escape-string-regexp@1.0.5
├─ escope@3.6.0
├─ esprima@4.0.0
├─ esrecurse@4.2.0
├─ estraverse@4.2.0
├─ esutils@2.0.2
├─ event-emitter@0.3.5
├─ events@1.1.1
├─ evp_bytestokey@1.0.3
├─ execa@0.7.0
├─ expand-brackets@0.1.5
├─ expand-range@1.8.2
├─ extend@3.0.1
├─ extglob@0.3.2
├─ extract-text-webpack-plugin@3.0.2
├─ extsprintf@1.3.0
├─ fast-deep-equal@1.0.0
├─ fast-json-stable-stringify@2.0.0
├─ fastparse@1.1.1
├─ file-loader@0.11.2
├─ filename-regex@2.0.1
├─ fill-range@2.2.3
├─ find-cache-dir@1.0.0
├─ find-up@2.1.0
├─ flatten@1.0.2
├─ for-in@1.0.2
├─ for-own@1.0.0
├─ forever-agent@0.6.1
├─ form-data@2.3.1
├─ fraction.js@4.0.2
├─ fs-extra@0.30.0
├─ fs.realpath@1.0.0
├─ fstream@1.0.11
├─ function-bind@1.1.1
├─ gauge@2.7.4
├─ gaze@1.1.2
├─ get-caller-file@1.0.2
├─ get-stdin@4.0.1
├─ get-stream@3.0.0
├─ getpass@0.1.7
├─ glob-base@0.3.0
├─ glob-parent@2.0.0
├─ glob@7.1.2
├─ globals@9.18.0
├─ globule@1.2.0
├─ gonzales-pe@4.2.3
├─ graceful-fs@4.1.11
├─ har-schema@2.0.0
├─ har-validator@5.0.3
├─ has-ansi@2.0.0
├─ has-flag@2.0.0
├─ has-unicode@2.0.1
├─ has@1.0.1
├─ hash-base@2.0.2
├─ hash.js@1.1.3
├─ hmac-drbg@1.0.1
├─ hoek@4.2.0
├─ home-or-tmp@2.0.0
├─ hosted-git-info@2.5.0
├─ html-comment-regex@1.1.1
├─ http-signature@1.2.0
├─ https-browserify@0.0.1
├─ icss-replace-symbols@1.1.0
├─ icss-utils@2.1.0
├─ ieee754@1.1.8
├─ in-publish@2.0.0
├─ indent-string@2.1.0
├─ indexes-of@1.0.1
├─ indexof@0.0.1
├─ inflight@1.0.6
├─ inherits@2.0.3
├─ interpret@1.0.4
├─ invariant@2.2.2
├─ invert-kv@1.0.0
├─ is-absolute-url@2.1.0
├─ is-arrayish@0.3.1
├─ is-binary-path@1.0.1
├─ is-buffer@1.1.6
├─ is-builtin-module@1.0.0
├─ is-directory@0.3.1
├─ is-dotfile@1.0.3
├─ is-equal-shallow@0.1.3
├─ is-extendable@0.1.1
├─ is-extglob@1.0.0
├─ is-finite@1.0.2
├─ is-fullwidth-code-point@1.0.0
├─ is-glob@2.0.1
├─ is-number@2.1.0
├─ is-plain-obj@1.1.0
├─ is-plain-object@2.0.4
├─ is-posix-bracket@0.1.1
├─ is-primitive@2.0.0
├─ is-stream@1.1.0
├─ is-svg@2.1.0
├─ is-typedarray@1.0.0
├─ is-utf8@0.2.1
├─ isarray@1.0.0
├─ isexe@2.0.0
├─ isnumeric@0.2.0
├─ isobject@3.0.1
├─ isstream@0.1.2
├─ javascript-natural-sort@0.7.1
├─ js-base64@2.3.2
├─ js-tokens@3.0.2
├─ js-yaml@3.10.0
├─ jsbn@0.1.1
├─ jsesc@1.3.0
├─ json-loader@0.5.7
├─ json-schema-traverse@0.3.1
├─ json-schema@0.2.3
├─ json-stringify-safe@5.0.1
├─ json5@0.5.1
├─ jsonfile@2.4.0
├─ jsprim@1.4.1
├─ kind-of@3.2.2
├─ klaw@1.3.1
├─ lazy-cache@0.2.7
├─ lcid@1.0.0
├─ load-json-file@1.1.0
├─ loader-runner@2.3.0
├─ loader-utils@1.1.0
├─ locate-path@2.0.0
├─ lodash._baseassign@3.2.0
├─ lodash._basecopy@3.0.1
├─ lodash._bindcallback@3.0.1
├─ lodash._createassigner@3.1.1
├─ lodash._getnative@3.9.1
├─ lodash._isiterateecall@3.0.9
├─ lodash._reinterpolate@3.0.0
├─ lodash.assign@4.2.0
├─ lodash.camelcase@4.3.0
├─ lodash.clonedeep@4.5.0
├─ lodash.defaults@4.2.0
├─ lodash.isarguments@3.1.0
├─ lodash.isarray@3.0.4
├─ lodash.keys@3.1.2
├─ lodash.memoize@4.1.2
├─ lodash.mergewith@4.6.0
├─ lodash.restparam@3.6.1
├─ lodash.tail@4.1.1
├─ lodash.template@4.4.0
├─ lodash.templatesettings@4.1.0
├─ lodash.uniq@4.5.0
├─ lodash@4.17.4
├─ longest@1.0.1
├─ loose-envify@1.3.1
├─ loud-rejection@1.6.0
├─ lru-cache@4.1.1
├─ macaddress@0.2.8
├─ make-dir@1.1.0
├─ map-obj@1.0.1
├─ math-expression-evaluator@1.2.17
├─ mathjs@3.16.5
├─ md5.js@1.3.4
├─ mem@1.1.0
├─ memory-fs@0.4.1
├─ meow@3.7.0
├─ micromatch@2.3.11
├─ miller-rabin@4.0.1
├─ mime-db@1.30.0
├─ mime-types@2.1.17
├─ mimic-fn@1.1.0
├─ minimalistic-assert@1.0.0
├─ minimalistic-crypto-utils@1.0.1
├─ minimatch@3.0.4
├─ minimist@1.2.0
├─ mixin-object@2.0.1
├─ mkdirp@0.5.1
├─ ms@2.0.0
├─ nan@2.7.0
├─ node-gyp@3.6.2
├─ node-libs-browser@2.0.0
├─ node-sass@4.6.0
├─ nopt@3.0.6
├─ normalize-package-data@2.4.0
├─ normalize-path@2.1.1
├─ normalize-range@0.1.2
├─ normalize-url@1.9.1
├─ npm-run-path@2.0.2
├─ npmlog@4.1.2
├─ num2fraction@1.2.2
├─ number-is-nan@1.0.1
├─ oauth-sign@0.8.2
├─ object-assign@4.1.1
├─ object-path@0.9.2
├─ object.omit@2.0.1
├─ once@1.4.0
├─ onecolor@3.0.4
├─ os-browserify@0.2.1
├─ os-homedir@1.0.2
├─ os-locale@2.1.0
├─ os-tmpdir@1.0.2
├─ osenv@0.1.4
├─ p-finally@1.0.0
├─ p-limit@1.1.0
├─ p-locate@2.0.0
├─ pako@0.2.9
├─ parse-asn1@5.1.0
├─ parse-glob@3.0.4
├─ parse-json@2.2.0
├─ path-browserify@0.0.0
├─ path-complete-extname@0.1.0
├─ path-exists@2.1.0
├─ path-is-absolute@1.0.1
├─ path-key@2.0.1
├─ path-parse@1.0.5
├─ path-type@1.1.0
├─ pbkdf2@3.0.14
├─ performance-now@2.1.0
├─ pify@2.3.0
├─ pinkie-promise@2.0.1
├─ pinkie@2.0.4
├─ pixrem@4.0.1
├─ pkg-dir@2.0.0
├─ pleeease-filters@4.0.0
├─ postcss-apply@0.8.0
├─ postcss-attribute-case-insensitive@2.0.0
├─ postcss-calc@6.0.1
├─ postcss-color-function@4.0.1
├─ postcss-color-gray@4.0.0
├─ postcss-color-hex-alpha@3.0.0
├─ postcss-color-hsl@2.0.0
├─ postcss-color-hwb@3.0.0
├─ postcss-color-rebeccapurple@3.0.0
├─ postcss-color-rgb@2.0.0
├─ postcss-color-rgba-fallback@3.0.0
├─ postcss-colormin@2.2.2
├─ postcss-convert-values@2.6.1
├─ postcss-cssnext@3.0.2
├─ postcss-custom-media@6.0.0
├─ postcss-custom-properties@6.2.0
├─ postcss-custom-selectors@4.0.1
├─ postcss-discard-comments@2.0.4
├─ postcss-discard-duplicates@2.1.0
├─ postcss-discard-empty@2.1.0
├─ postcss-discard-overridden@0.1.1
├─ postcss-discard-unused@2.2.3
├─ postcss-filter-plugins@2.0.2
├─ postcss-font-family-system-ui@2.0.1
├─ postcss-font-variant@3.0.0
├─ postcss-image-set-polyfill@0.3.5
├─ postcss-initial@2.0.0
├─ postcss-load-config@1.2.0
├─ postcss-load-options@1.2.0
├─ postcss-load-plugins@2.3.0
├─ postcss-loader@2.0.8
├─ postcss-media-minmax@3.0.0
├─ postcss-media-query-parser@0.2.3
├─ postcss-merge-idents@2.1.7
├─ postcss-merge-longhand@2.0.2
├─ postcss-merge-rules@2.1.2
├─ postcss-message-helpers@2.0.0
├─ postcss-minify-font-values@1.0.5
├─ postcss-minify-gradients@1.0.5
├─ postcss-minify-params@1.2.2
├─ postcss-minify-selectors@2.1.1
├─ postcss-modules-extract-imports@1.1.0
├─ postcss-modules-local-by-default@1.2.0
├─ postcss-modules-scope@1.1.0
├─ postcss-modules-values@1.3.0
├─ postcss-nesting@4.2.1
├─ postcss-normalize-charset@1.1.1
├─ postcss-normalize-url@3.0.8
├─ postcss-ordered-values@2.2.3
├─ postcss-pseudo-class-any-link@4.0.0
├─ postcss-pseudoelements@5.0.0
├─ postcss-reduce-idents@2.4.0
├─ postcss-reduce-initial@1.0.1
├─ postcss-reduce-transforms@1.0.4
├─ postcss-replace-overflow-wrap@2.0.0
├─ postcss-sass@0.1.0
├─ postcss-scss@1.0.2
├─ postcss-selector-matches@3.0.1
├─ postcss-selector-not@3.0.1
├─ postcss-selector-parser@2.2.3
├─ postcss-smart-import@0.7.5
├─ postcss-svgo@2.1.6
├─ postcss-unique-selectors@2.0.2
├─ postcss-value-parser@3.3.0
├─ postcss-zindex@2.2.0
├─ postcss@6.0.14
├─ prepend-http@1.0.4
├─ preserve@0.2.0
├─ private@0.1.8
├─ process-nextick-args@1.0.7
├─ process@0.11.10
├─ promise-each@2.2.0
├─ prr@0.0.0
├─ pseudomap@1.0.2
├─ public-encrypt@4.0.0
├─ punycode@1.4.1
├─ q@1.5.1
├─ qs@6.5.1
├─ query-string@4.3.4
├─ querystring-es3@0.2.1
├─ querystring@0.2.0
├─ rails-erb-loader@5.2.1
├─ randomatic@1.1.7
├─ randombytes@2.0.5
├─ randomfill@1.0.3
├─ read-cache@1.0.0
├─ read-pkg-up@1.0.1
├─ read-pkg@1.1.0
├─ readable-stream@2.3.3
├─ readdirp@2.1.0
├─ redent@1.0.0
├─ reduce-css-calc@1.3.0
├─ reduce-function-call@1.0.2
├─ regenerate@1.3.3
├─ regenerator-runtime@0.10.5
├─ regenerator-transform@0.10.1
├─ regex-cache@0.4.4
├─ regex-parser@2.2.8
├─ regexpu-core@1.0.0
├─ regjsgen@0.2.0
├─ regjsparser@0.1.5
├─ remove-trailing-separator@1.1.0
├─ repeat-element@1.1.2
├─ repeat-string@1.6.1
├─ repeating@2.0.1
├─ request@2.83.0
├─ require-directory@2.1.1
├─ require-from-string@1.2.1
├─ require-main-filename@1.0.1
├─ resolve-url-loader@2.2.0
├─ resolve-url@0.2.1
├─ resolve@1.5.0
├─ rework-visit@1.0.0
├─ rework@1.0.1
├─ rgb-hex@2.1.0
├─ rgb@0.1.0
├─ right-align@0.1.3
├─ rimraf@2.6.2
├─ ripemd160@2.0.1
├─ safe-buffer@5.1.1
├─ sass-graph@2.2.4
├─ sass-loader@6.0.6
├─ sax@1.2.4
├─ schema-utils@0.3.0
├─ scss-tokenizer@0.2.3
├─ seed-random@2.2.0
├─ semver@5.4.1
├─ set-blocking@2.0.0
├─ set-immediate-shim@1.0.1
├─ setimmediate@1.0.5
├─ sha.js@2.4.9
├─ shallow-clone@0.1.2
├─ shebang-command@1.2.0
├─ shebang-regex@1.0.0
├─ signal-exit@3.0.2
├─ simple-swizzle@0.2.2
├─ slash@1.0.0
├─ sort-keys@1.1.2
├─ source-list-map@2.0.0
├─ source-map-resolve@0.3.1
├─ source-map-support@0.4.18
├─ source-map-url@0.3.0
├─ source-map@0.5.7
├─ spdx-correct@1.0.2
├─ spdx-expression-parse@1.0.4
├─ spdx-license-ids@1.2.2
├─ sprintf-js@1.0.3
├─ sshpk@1.13.1
├─ stdout-stream@1.4.0
├─ stream-browserify@2.0.1
├─ stream-http@2.7.2
├─ strict-uri-encode@1.1.0
├─ string_decoder@0.10.31
├─ string-width@1.0.2
├─ stringstream@0.0.5
├─ strip-ansi@3.0.1
├─ strip-bom@2.0.0
├─ strip-eof@1.0.0
├─ strip-indent@1.0.1
├─ style-loader@0.18.2
├─ sugarss@1.0.1
├─ supports-color@4.5.0
├─ svgo@0.7.2
├─ tapable@0.2.8
├─ tar@2.2.1
├─ timers-browserify@2.0.4
├─ tiny-emitter@2.0.0
├─ to-arraybuffer@1.0.1
├─ to-fast-properties@1.0.3
├─ tough-cookie@2.3.3
├─ trim-newlines@1.0.0
├─ trim-right@1.0.1
├─ tty-browserify@0.0.0
├─ tunnel-agent@0.6.0
├─ tweetnacl@0.14.5
├─ typed-function@0.10.5
├─ uglify-js@2.8.29
├─ uglify-to-browserify@1.0.2
├─ uglifyjs-webpack-plugin@0.4.6
├─ uniq@1.0.1
├─ uniqid@4.1.1
├─ uniqs@2.0.0
├─ units-css@0.4.0
├─ urix@0.1.0
├─ url@0.11.0
├─ util-deprecate@1.0.2
├─ util@0.10.3
├─ uuid@3.1.0
├─ validate-npm-package-license@3.0.1
├─ vendors@1.0.1
├─ verror@1.10.0
├─ viewport-dimensions@0.2.0
├─ vm-browserify@0.0.4
├─ watchpack@1.4.0
├─ webpack-manifest-plugin@1.3.2
├─ webpack-sources@1.0.2
├─ webpack@3.8.1
├─ whet.extend@0.9.9
├─ which-module@2.0.0
├─ which@1.3.0
├─ wide-align@1.1.2
├─ window-size@0.1.0
├─ wordwrap@0.0.2
├─ wrap-ansi@2.1.0
├─ wrappy@1.0.2
├─ xtend@4.0.1
├─ y18n@3.2.1
├─ yallist@2.1.2
├─ yargs-parser@7.0.0
└─ yargs@8.0.2
Done in 110.98s.
Installing dev server for live reloading
         run  yarn add --dev webpack-dev-server from "."
yarn add v1.3.2
[1/4] Resolving packages...
[2/4] Fetching packages...
info fsevents@1.1.2: The platform "linux" is incompatible with this module.
info "fsevents@1.1.2" is an optional dependency and failed compatibility check. Excluding it from installation.
[3/4] Linking dependencies...
warning "@rails/webpacker > postcss-cssnext@3.0.2" has unmet peer dependency "caniuse-lite@^1.0.30000697".
warning "webpack-dev-server > webpack-dev-middleware@1.12.0" has unmet peer dependency "webpack@^1.0.0 || ^2.0.0 || ^3.0.0".
warning " > webpack-dev-server@2.9.4" has unmet peer dependency "webpack@^2.2.0 || ^3.0.0".
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 117 new dependencies.
├─ accepts@1.3.4
├─ ansi-html@0.0.7
├─ array-flatten@1.1.1
├─ array-includes@3.0.3
├─ array-union@1.0.2
├─ array-uniq@1.0.3
├─ batch@0.6.1
├─ body-parser@1.18.2
├─ bonjour@3.5.0
├─ buffer-indexof@1.1.1
├─ bytes@3.0.0
├─ compressible@2.0.12
├─ compression@1.7.1
├─ connect-history-api-fallback@1.4.0
├─ content-disposition@0.5.2
├─ content-type@1.0.4
├─ cookie-signature@1.0.6
├─ cookie@0.3.1
├─ deep-equal@1.0.1
├─ define-properties@1.1.2
├─ del@3.0.0
├─ depd@1.1.1
├─ destroy@1.0.4
├─ detect-node@2.0.3
├─ dns-equal@1.0.0
├─ dns-packet@1.2.2
├─ dns-txt@2.0.2
├─ ee-first@1.1.1
├─ encodeurl@1.0.1
├─ es-abstract@1.9.0
├─ es-to-primitive@1.1.1
├─ escape-html@1.0.3
├─ etag@1.8.1
├─ eventemitter3@1.2.0
├─ eventsource@0.1.6
├─ express@4.16.2
├─ faye-websocket@0.10.0
├─ finalhandler@1.1.0
├─ foreach@2.0.5
├─ forwarded@0.1.2
├─ fresh@0.5.2
├─ globby@6.1.0
├─ handle-thing@1.2.5
├─ hpack.js@2.1.6
├─ html-entities@1.2.1
├─ http-deceiver@1.2.7
├─ http-errors@1.6.2
├─ http-parser-js@0.4.9
├─ http-proxy-middleware@0.17.4
├─ http-proxy@1.16.2
├─ iconv-lite@0.4.19
├─ import-local@0.1.1
├─ internal-ip@1.2.0
├─ ip@1.1.5
├─ ipaddr.js@1.5.2
├─ is-callable@1.1.3
├─ is-date-object@1.0.1
├─ is-path-cwd@1.0.0
├─ is-path-in-cwd@1.0.0
├─ is-path-inside@1.0.0
├─ is-regex@1.0.4
├─ is-symbol@1.0.1
├─ is-wsl@1.1.0
├─ json3@3.3.2
├─ killable@1.0.0
├─ loglevel@1.5.1
├─ media-typer@0.3.0
├─ merge-descriptors@1.0.1
├─ methods@1.1.2
├─ mime@1.4.1
├─ multicast-dns-service-types@1.1.0
├─ multicast-dns@6.1.1
├─ negotiator@0.6.1
├─ node-forge@0.6.33
├─ object-keys@1.0.11
├─ obuf@1.1.1
├─ on-finished@2.3.0
├─ on-headers@1.0.1
├─ opn@5.1.0
├─ original@1.0.0
├─ p-map@1.2.0
├─ parseurl@1.3.2
├─ path-is-inside@1.0.2
├─ path-to-regexp@0.1.7
├─ portfinder@1.0.13
├─ proxy-addr@2.0.2
├─ querystringify@1.0.0
├─ range-parser@1.2.0
├─ raw-body@2.3.2
├─ requires-port@1.0.0
├─ resolve-cwd@2.0.0
├─ resolve-from@3.0.0
├─ select-hose@2.0.0
├─ selfsigned@1.10.1
├─ send@0.16.1
├─ serve-index@1.9.1
├─ serve-static@1.13.1
├─ setprototypeof@1.1.0
├─ sockjs-client@1.1.4
├─ sockjs@0.3.18
├─ spdy-transport@2.0.20
├─ spdy@3.4.7
├─ statuses@1.3.1
├─ thunky@0.1.0
├─ time-stamp@2.0.0
├─ type-is@1.6.15
├─ unpipe@1.0.0
├─ url-parse@1.2.0
├─ utils-merge@1.0.1
├─ vary@1.1.2
├─ wbuf@1.7.2
├─ webpack-dev-middleware@1.12.0
├─ webpack-dev-server@2.9.4
├─ websocket-driver@0.7.0
├─ websocket-extensions@0.1.2
├─ yargs-parser@4.2.1
└─ yargs@6.6.0
Done in 91.25s.
Webpacker successfully installed 🎉 🍰
       rails  webpacker:install:vue
Webpack binstubs not found.
Have you run rails webpacker:install ?
Make sure the bin directory or binstubs are not included in .gitignore
Exiting!
         run  bundle exec spring binstub --all
* bin/rake: spring inserted
* bin/rails: spring inserted
```
