## [v1.4.0](https://github.com/cucumber/cucumber-rails/compare/v1.3.1...v1.4.0) (2013-08-23)

### New Features

 * Rails 4 compatibility
 * Removal of unused tests (routing, multiple_databases, pre_bundler and mongo)
 * New test raising_errors.feature to test raising routing errors that replaced the earlier routing.feature
 * Added recommendation in README.md for running install scripts after upgrading (Joost Baaij)


## [v1.3.1](https://github.com/cucumber/cucumber-rails/compare/v1.3.0...v1.3.1) (2013-03-15)

### New Features

* Multiple-gemfile testing and travis configuration ([#240](https://github.com/cucumber/cucumber-rails/pull/240) Simon Coffey)

### Changed Features

* Fix a typo in a template ([#228](https://github.com/cucumber/cucumber-rails/pull/228) Robin Dupret)
* Depend upon the generic test:prepare task ([#230](https://github.com/cucumber/cucumber-rails/pull/230) Graeme Mathieson)
* Allow users to disable database_cleaner hooks ([#232](https://github.com/cucumber/cucumber-rails/pull/232)  Simon Coffey)
* Rails 4.0.0-beta ActionController::Integration depreciation fix ([#234](https://github.com/cucumber/cucumber-rails/pull/234) Daniel Bruns)

## [v1.3.0](https://github.com/cucumber/cucumber-rails/compare/v1.2.1...v1.3.0) (2012-02-19)

### New Features

* JavaScript database strategies should take options ([#192](https://github.com/cucumber/cucumber-rails/issues/192), [#195](https://github.com/cucumber/cucumber-rails/pull/195) Thomas Walpole)

### Changed features

* select_date arguments should be reversed ([#190](https://github.com/cucumber/cucumber-rails/issues/190), [#191](https://github.com/cucumber/cucumber-rails/pull/191) Gavin Hughes)

## [v1.2.1](https://github.com/cucumber/cucumber-rails/compare/v1.2.0...v1.2.1) (2011-12-04)

### New features

* Allow ability to use deletion as a javascript database strategy ([#185](https://github.com/cucumber/cucumber-rails/pull/185) Thijs de Vries)
* Support custom JS strategies ([#184](https://github.com/cucumber/cucumber-rails/pull/184) Michael Pabst)

## [v1.2.0](https://github.com/cucumber/cucumber-rails/compare/v1.1.1...v1.2.0) (2011-11-03)

### Removed features
* The (deprecated) tableish method has been removed. See https://gist.github.com/1299371 for an alternative. (Aslak Helles??y)

### Bugfixes
* Non-threadsafe database connections shared between threads ([#166](https://github.com/cucumber/cucumber-rails/issues/166) Matt Wynne)

## [v1.1.1](https://github.com/cucumber/cucumber-rails/compare/v1.1.0...v1.1.1) (2011-10-03)

### Removed features

The `cucumber:feature` generator has been removed. The reasoning behind this is the same as for
removing `web_steps.rb`,  `paths.rb` and  `selectors.rb` in v1.1.0.

## [v1.1.0](https://github.com/cucumber/cucumber-rails/compare/v1.0.6...v1.1.0) (2011-09-28)

### Removed features

The following files will no longer be generated if you are running `rails generate cucumber:install`:

* features/step_definitions/web_steps.rb
* features/support/paths.rb
* features/support/selectors.rb

The reason behind this is that the steps defined in `web_steps.rb` leads people to write scenarios of a
very imperative nature that are hard to read and hard to maintain. Cucumber scenarios should not be a series
of steps that describe what a user clicks. Instead, they should express what a user *does*. Example:

    Given I have signed up as "user@host.com"

with a Step Definition that perhaps looks like this:

    Given /^I have signed up as "([^"]*)"$/ do |email|
      visit(signup_path)
      fill_in('Email', :with => email)
      fill_in('Password', :with => 's3cr3t')
      fill_in('Password Confirmation', :with => 's3cr3t')
      click_button('Sign up')
    end

Moving user interface details from the scenarios and down to the step definitions makes scenarios
much easier to read. If you change the user interface you only have to change a step definition or two
instead of a lot of scenarios that explicitly describe how to sign up.

You can learn more about the reasoning behind this change at the following links:

* [Cucumber mailing list: Removing web_steps.rb in Cucumber 1.1.0](http://groups.google.com/group/cukes/browse_thread/thread/26f80b93c94f2952)
* [Cucumber-Rails issue #174: Remove web_steps.rb since it encourages people to write poor tests.](https://github.com/cucumber/cucumber-rails/issues/174)
* [Refuctoring your Cukes by Matt Wynne](http://skillsmatter.com/podcast/home/refuctoring-your-cukes)
* [Imperative vs Declarative Scenarios in User Stories by Ben Mabey](http://benmabey.com/2008/05/19/imperative-vs-declarative-scenarios-in-user-stories.html)
* [Whose domain is it anyway? by Dan North](http://dannorth.net/2011/01/31/whose-domain-is-it-anyway/)
* [You're Cuking it Wrong by Jonas Nicklas](http://elabs.se/blog/15-you-re-cuking-it-wrong)

You can learn more about what Capybara has to offer in Capybara's [README](https://github.com/jnicklas/capybara).

## [v1.0.6](https://github.com/cucumber/cucumber-rails/compare/v1.0.5...v1.0.6) (2011-09-25)

### Bugfixes
* Fix deprecation warnings ([#169](https://github.com/cucumber/cucumber-rails/issues/169), [#170](https://github.com/cucumber/cucumber-rails/pull/170) Micah Geisel)
* Deprecate #tableish. The Capybara::Node::Finders API has obsoleted the need for it. ([#145](https://github.com/cucumber/cucumber-rails/issues/145) Aslak Helles??y)

## [v1.0.5](https://github.com/cucumber/cucumber-rails/compare/v1.0.4...v1.0.5) (2011-09-14)

### Bugfixes
* No = dependencies in gemspec, since rubies with old YAML (sych) can't read them. (Aslak Helles??y)

## [v1.0.4](https://github.com/cucumber/cucumber-rails/compare/v1.0.3...v1.0.4) (2011-09-12)

### Bugfixes
* Active_record hook prevents features that access multiple database from running correctly ([#152](https://github.com/cucumber/cucumber-rails/issues/152) winnipegtransit)

## [v1.0.3](https://github.com/cucumber/cucumber-rails/compare/v1.0.2...v1.0.3) (2011-09-11)

### Bugfixes
* sqlite3-ruby is now sqlite3 ([#158](https://github.com/cucumber/cucumber-rails/pull/158) Trung Le)
* Broken link in the USAGE file of the features generator ([#156](https://github.com/cucumber/cucumber-rails/pull/156) Pablo Alonso Garc??a)
* Rails destroy cucumber:feature deletes the steps folder, even though it's not empty. ([#154](https://github.com/cucumber/cucumber-rails/pull/154]), [#111](https://github.com/cucumber/cucumber-rails/issues/111) mblake)
* Adjust select_date, select_time xpaths so they work when scoped in the document ([#151](https://github.com/cucumber/cucumber-rails/pull/151) Thomas Walpole)
* Extend javascript emulation to handle rails CSRF protection ([#164](https://github.com/cucumber/cucumber-rails/pull/164) Jonathon M. Abbott)
* Add steps for finding fields with errors ([#162](https://github.com/cucumber/cucumber-rails/pull/162) Mike Burns)

## [v1.0.2](https://github.com/cucumber/cucumber-rails/compare/v1.0.1...v1.0.2) (2011-06-26)

### Bugfixes
* Removed the dependency on rack-test, since it is not used directly. v1.0.1 was incompatible with Rails 3.0.9. (Aslak Helles??y)

## [v1.0.1](https://github.com/cucumber/cucumber-rails/compare/v1.0.0...v1.0.1) (2011-06-25)

### New Features
* Added a @no-database-cleaner tag you can add if you don't want to run DatabaseCleaner. Useful for debugging if you want to leave data in the database. Typical use case is to run `rails server --environment test` to look at/try app with data from test. (Aslak Helles??y)
* History file is now in Markdown format. (Aslak Helles??y)

## [v1.0.0](https://github.com/cucumber/cucumber-rails/compare/v0.5.2...v1.0.0) (2011-06-20)

### New Features
* Upgraded Cucumber dependency to 1.0.0. (Aslak Helles??y)

## [v0.5.2](https://github.com/cucumber/cucumber-rails/compare/v0.5.1...v0.5.2) (2011-06-07)

### New Features
* Upgraded to Capybara 1.0.0.rc1 (Aslak Helles??y)
* Add stats to generator (#144 Aslak Helles??y)

## [v0.5.1](https://github.com/cucumber/cucumber-rails/compare/v0.5.0...v0.5.1) (2011-05-25)

### Bugfixes
* Mixed DB access feature for @javascript drivers (#142 Alexander Mankuta)
* cucumber:feature and integers. not creating feature correctly (#30 John Ivanoff, Aslak Helles??y)
* New project can't find capybara's "visit" (#143 Aslak Helles??y)
* rails generate cucumber:install attempts double run (#140 Aslak Helles??y)

## [v0.5.0](https://github.com/cucumber/cucumber-rails/compare/v0.5.0.beta1...v0.5.0) (2011-05-17)

### Bugfixes
* undefined method `add_assertion' for nil:NilClass (#96, #97, #98 Aslak Helles??y)
* Capybara name error from env.rb (#125 Aslak Helles??y)
* Fixed date-localization bug (#138 Michael Opitz)

## [v0.5.0.beta1](https://github.com/cucumber/cucumber-rails/compare/v0.4.1...v0.5.0.beta1) (2011-05-09)

### Removed features
* Dropped support for Rails 2 (Aslak Helles??y)
* Dropped support for Webrat (Aslak Helles??y)
* Removed database cleaner strategy overrides (#134 Daniel Morrison, Daniel Duvall)

### Improvements
* Upgrade to Capybara 1.0.0.beta1 or newer (#129, #130 Simon Menke, Klaus Hartl, Aslak Helles??y)
* Generated paths.rb cleanup (#133 Tim Pope)
* Allow css pseudo-classes in scopers (#122 twalpole)

## [v0.4.1](https://github.com/cucumber/cucumber-rails/compare/v0.4.0...v0.4.1) (2011-04-05)

### Bugfixes
* Fixed incorrect warning in generated files. (#115 Emanuele Vicentini)
* Fixed incorrect hooks for DatabaseCleaner (#113 Markus Bengts)
* Throw an error if the user forgot to add DatabaseCleaner to the Gemfile, allowing them to decide whether or not to use it. (#36 Aslak Helles??y, Ryan Bigg)

## [v0.4.0](https://github.com/cucumber/cucumber-rails/compare/v0.3.2...v0.4.0) (2011-03-20)

### New Features
* Add selectors helper (#63 Bodaniel Jeanes)
* Capybara date stepdefs (#66 Rob Holland)
* The World now includes Rack::Test::Methods, allowing get, post, put delete (Aslak Helles??y)

### Bugfixes
* Allow setting rails root (#102, #103, Fabio Kreusch)
* Fix Date selection steps and helpers (#93, #99, #100, #101, #109 James Herdman, John Ferlito, twalpole, Geoff Drake, Ricky Robinson, Michael Fleet)
* Can not run cucumber-rails (0.4.0.beta.1) with cucumber (0.10.0) (#89 Aslak Helles??y)
* Installing cucumber-rails without a database.yml fails (#61 Aslak Helles??y)
* Fix #click_link compatibility with Capybara 0.4. (#54, #77, #78, #80 Aslak Helles??y)
* Support for projects using other ORMs than ActiveRecord (or nothing at all). (#18, #22, #46, #85, #86, #87, #90 Aslak Helles??y)
* @allow-rescue not working in rails 3 (#31 Joe Ferris, Aslak Helles??y)
* Gem dependency on Nokogiri (for #tableish). (#53 Aslak Helles??y)

### Removed Features
* Automatic detection of RSpec, Capybara and Webrat for install generator. Set gems explicitly in your Gemfile (Rails3) or environment.rb (Rails2)
* Then /^(?:|I )should see JSON:$/. Use #get and #last_response instead. See features/rails3.feature. (Aslak Helles??y)
* Cucumber::Rails::World.use_transactional_fixtures. TODO: Explain what to do instead.
  No more Cucumber::Rails::World.use_transactional_fixtures = false. Use DatabaseCleaner.strategy = :none instead

## [v0.3.2](https://github.com/cucumber/cucumber-rails/compare/v0.3.1...v0.3.2) (2010-06-06) The `rails-2.3.x` support branch branches off from here.
* web_steps.rb uses "([^"]*)" instead of "([^\"]*)" (Aslak Helles??y)
* Renamed cucumber:skeleton to cucumber:install (Rails 3 generator). (Aslak Helles??y)
* Upgraded to be compatible with rspec 2.0.0.beta.10 (#35 Gabor Ratky, Pete Yandell)

## [v0.3.1](https://github.com/cucumber/cucumber-rails/compare/v0.3.0...v0.3.1) (2010-05-04)

This release has a lot of bugfixes! The test suite (based on Aruba) verifies that Cucumber-Rails
now works with various combinations of: 

* Cucumber 0.6.x/0.7.2
* Rails2/Rails3
* RSpec1/RSpec2/Test-Unit/Mini-Uint
* Webrat/CapyBara
* MRI 1.8.6/1.8.7/1.9.1

This one requires a special mention: The handy (but error prone) rerun functionality has moved to a 
separate rerun profile, so all rerun.txt related issues should now be gone.

* New Capybara Step Definitions for Dates. (Rob Holland)
* Steps now recognise "Given I am on the users page" etc. (Solomon White)
* Relegate rerun to its own profile and rake task (Mike Sassak)
* Added new Then /^(?:|I )should see JSON:$/ step definition to Capybara - useful for REST. (Aslak Helles??y)
* The #tableish method now understands tables with colspan and rowspan
* Support RSpec 2 (Johan Kiviniemi, Aslak Helles??y, Rolf Bjaanes)
* Added @no-js-emulation, which turns off javascript emulation for delete links when not using browser testing. (Rob Holland, Aslak Helles??y)
* Korean translation (Shim Taewon)

### Bugfixes
* No longer need to install the test-unit gem on 1.9.1 (Aslak Helles??y)
* capybara rack-test field should contain step support for textarea (#28 Nicholas Rutherford)
* "Rspec is not missing constant Matchers!" error. (#27 David Chelimsky, Aslak Helles??y)
* @culerity tag breaks Rails 3 RESTful helpers (#17 Aslak Helles??y)

## [v0.3.0](https://github.com/cucumber/cucumber-rails/compare/v0.2.4...v0.3.0) (2010-02-26)

This is a major release since we're now supporting both Rails 3 and RSpec 2. Older versions
(Rails 2 and RSpec 1) are still supported.

### New Features
* Support for both Rails-2.x and Rails-3.x (#10 Kristian Mandrup, Aleksey Gureiev, Ashley Moran, Aslak Helles??y)
* Support for both RSpec-1.x and RSpec-2.x (Louis Rose, Aslak Helles??y)
* Features will default to Javascript emulation unless you turn it off with @culerity,  (Aslak Helles??y)
* Japanese translation. (MOROHASHI Kyosuke)

### Bugfixes
* Support projects that don't use ActiveRecord (#14 Aslak Helles??y)
* Running test/unit tests when creating a skeleton (#12 Aleksey Gureiev)
* Inform that config/database.yml is overwritten, be smarter about it and inform the user that it is forced. (#15 Aslak Helles??y)
* Reverts changes from issue #5 where verification of query string params was added to the step for being on a page.  Adds step discussed in issue #11 for verification of query string. (#5, #11 Eric Milford)
* Fixed typos in Capybara's web steps (has_not_xpath? => has_no_xpath?) (Thorbj??rn Hermansen, Carlos Antonio da Silva)


### New Features
* Added Danish translation (Kristian Mandrup)
* Using Gemfile for Rails 3. Tidies it up and adds cucumber gems only if not already present! (Kristian Mandrup)
* Added Generators wrapper module for Rails 3 generators so they are now all in Cucumber::Generators (Kristian Mandrup)

### Bugfixes
* Started to work on solutions for generating suitable support files depending on Rails version
  - see skeleton_base.rb#create_feature_support and templates/support  

## [v0.2.4](https://github.com/cucumber/cucumber-rails/compare/v0.2.3...v0.2.4) (2010-01-18)

### New Features
* Added Spanish translation (Gabriel)

### Bugfixes
* Fixed some broken Webrat/Test::Unit step definitions. (Aslak Helles??y)
* Better Javascript emulation with Capybara (#7 Thorbj??rn Hermansen)
* Removed stray quote in i18n web_steps.rb (Gabriel)
* Update hooks to new boolean logic (#6 Jon Larkowski, Michael MacDonald)
* Fixed incompatibility with Rails 3 (Mutwin Kraus)
* Fixed broken "fill in the following" step for Capybara web_steps (Lenny Marks)
* Capybara web_steps.rb with_scope didn't work in nested steps (Lenny Marks)
* Fixed "should not see" steps in web_steps.rb to use the correct selector (Toni Tuominen)

## [v0.2.3](https://github.com/cucumber/cucumber-rails/compare/v0.2.2...v0.2.3) (2010-01-03)

### New Features
* The #tableish Proc can return Strings as well as Nokogiri nodes now. (Aslak Helles??y)

### Bugfixes
* Handle all types of URIs in "I should be on ..." steps. (#5 Andrew D. Smith)

## [v0.2.2](https://github.com/cucumber/cucumber-rails/compare/v0.2.1...v0.2.2) (2009-12-21)

### Bugfixes
* Fix bad link in gemspec. (Aslak Helles??y)
* Unified file attaching step names. (Ji???? Zajpt)
* Fix typos in variable names in several step definitions. (Ji???? Zajpt)
* cucumber.rake finds the wrong vendored cucumber when a plugin name starts with "cucumber" (#4 James Herdman, Paco Benavent, Aslak Helles??y)

### New features
* Czech translations. (Ji???? Zajpt)

## [v0.2.1](https://github.com/cucumber/cucumber-rails/compare/v0.2.0...v0.2.1) (2009-12-16)

Small bugfix release

### Bugfixes
* Made sure database_cleaner is always set up as a dependency in config/environments/cucumber.rb. (Aslak Helles??y)


This is the first release of cucumber-rails, which was factored out of cucumber.
We're calling it 0.2.0 just because we did some prereleases in the 0.1 series,
and to celebrate that cucumber-rails now supports Capybara as an alternative to Webrat.

### UPGRADING FROM A PREVIOUS CUCUMBER SETUP

1. Remove your features/support/version_check.rb
1. Remove your features/step_definitions/webrat_steps.rb
   If you have added your own custom step definitions to this file,
   put them in a different file under features/step_definitions
1. run "ruby script/generate cucumber --help" to see what options you have.
1. run "ruby script/generate cucumber" - plus whatever options you think fit for you.
   Answer "n" (no) when asked to overwrite paths.rb.
   Answer "y" (yes) when asked to overwrite other files, but do "d" (diff) first.
   If you have edits in some of these files that you want to keep, store the diff
   in a temporary file and reapply after you have overwritten the file. ALso consider
   adding your custom code to another file that won't be overwritten the next time
   you upgrade.
   
   Many people have edits in their env.rb file. This is something you should try
   to avoid in the future. Instead, keep your custom setup in a different file
   under features/support - Cucumber loads all files under features/**/*.rb anyway.
   
   If you have a Spork setup, see the end of this thread:
   http://groups.google.com/group/cukes/browse_thread/thread/475385cc26377215

### New features
* Added an @emulate_rails_javascript tag that will emulate onclick with Capybara (Aslak Helles??y, Rob Holland)
* Added a smart config/cucumber.yml file that will rerun previously failing scenarios (Aslak Helles??y)
* Support for Capybara. Run "script/generate --capybara" if you want that. (Rob Holland, Aslak Helles??y)
* New #tableish method to extract table-like data from a HTML page. Pure Nokogiri/CSS3/XPath. (Aslak Helles??y)

### Bugfixes
* Webrat step "Then I should be on" should use request_uri instead of path for missing query string parameters (ZhangJinzhu)
* Added MIME type parameter to attach file step definition (Felix Flores)
* Added check when including ActiveSupport::Testing::SetupAndTeardown for older Rails versions (Jeremy Durham)
