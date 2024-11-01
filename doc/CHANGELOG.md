See doc/upgrading.md for the upgrade documentation!

## Version 2.6.0

## New features

* Ruby 3.0 is now supported.
* Support obsidian links in notes.

## Removed features

* No longer supporting EOL Ruby 2.5

### Bug fixes

* Fix Docker image functionality in certain cases.
* Lots of dependencies have been upgraded.
* Fixed some error messages in import.
* Fixed import in the Docker image.
* Footer shows the Git version hash and date in the Docker image

## Updated translations

* Finnish (by maintainer Jyri-Petteri ”ZeiP” Paloposki)
* Turkish (thanks Burak Ekseli!)
* Spanish (thanks Francisco Serrador!)

## Version 2.5.2

### New features

* Whole Tracks is now translatable.
* New Finnish locale by the maintainer Jyri-Petteri ”ZeiP” Paloposki.
* Update last login field when validating an existing login.
* Show more users in the user list and allow changing the order criteria.

### Bug fixes

* Fix tag-specific task lists to work in a multi-user environment.
* Fix setting the due date in the calendar view.
* Fix a bug causing 500 errors for users with different locales.
* Lots of dependencies have been upgraded.
* Better CI tests.
* Code style fixes.
* Small style issues.

## Version 2.5.1

### Security issue disclosure

Joe Thorpe from Secarma disclosed an XSS issue that was inadvertently
fixed in 2.5.0 by another bug fix. Tracks previously rendered XSS content
in the user's own data. The content is only shown to the user themself,
which mitigates the vulnerability in the normal use case where a single
user account is only used by one person. The CVSS rating for self-XSS is
debatable and thus is not published for this issue.

I want to thank Joe for reporting the issue and for the insightful discussion
regarding the issue. Thanks to the disclosure there is now also a written
security policy for the project.

### Bug fixes

* Editing a due date in the calendar view fixed
* Adding actions in the context view fixed
* Fixed the recurring todo UI

## Version 2.5.0

### New features
* Updated documentation both in the doc directory and online.
* .skip-docker file has been replaced with .use-docker, see upgrading.md for
  details.
* Added email, last login, creation and update time to the user model.
* Added terms of service and email fields to the signup form. The TOS link is
  defined in site.yml, see config/site.yml.tmpl.
* New, lighter default color scheme. The black color scheme is also available
  for selection in the user preferences. Default theme can be set in site.yml.
* Added a help page to the ? menu linking to online help assets.
* Allow the user to remove their own account.

### Removed features
* Ruby versions below 2.5 are no longer supported.
* Old Internet Explorer versions (7 and 8) are no longer supported.

### Bug fixes
* Fixed the signup form to use login form styles.
* Lots of dependencies have been upgraded, including Rails major upgrade.
* Fixed some minor UI bugs.

## Version 2.4.2

### New features
* The new todo UI form has been updated.

### Bug fixes
* Needless sanitization of tags has been removed.
* Security vulnerabilities have been fixed.

## Version 2.4.1

### Bug fixes
* Fixed a bug in the tag migration that prevented the migration from completing
  at least in some MySQL environments. The bug only affected upgrading an existing Tracks
  installation.

## Version 2.4.0

### New features
* Removed support for deprecated password-hashing algorithm. This
  eliminates config.salt. Note the addition of a pre-upgrade step to
  check for obsolete passwords.
* All tags now belong to a user. Existing tags are migrated to users based on
  the taggings and duplicated as necessary. If there's only one user, all unused tags are
  assigned to them, otherwise unused tags are removed.
* All REST APIs now also accept user token as password.
* The stats view now uses Charts.js instead of the Flash-based chart library.
* A Docker environment is used unless the .skip-docker file exists.
* Rails 5.2
* Thin replaces WEBrick as the included web server
* Tracks is tested on Ruby 2.4 and 2.5
* The MessageGateway will save the received email as an attachement to the todo
* Add a configuration option for serving static assets from Rails

### Removed features
* Ruby versions below 2.4 are no longer supported.

### Bug fixes
* Multiple fixes to REST APIs.
* Several UI bugs fixed.

## Version 2.3.0

### New and changed features
* Numerous bug fixes
* You can select to group todos on the home page by context or by
  project (using the view menu). This also works for tag page, the
  project page, the tickler and the context page
* You can now change the state of a context to closed
* Czech locale has been renamed from cz to cs to follow ISO standards
* Added Russian locale (@AlexStein)
* The toggle-notes and toggle-collapsed-containers have been moved into
  the view menu.
* The environment must now be specified during asset precompilation.
* Tracks is tested on Ruby 1.9.3, 2.0.0, and 2.1

### Removed features
* Ruby 1.8.x is no longer supported

### Under the hood
* Upgraded Rails to 4.1
* Several refactorings for easier maintenance

## Version 2.2.3

* Bug fixes

## Version 2.2.2

* Security fixes

## Version 2.2.1

* Bugfixes (including one that prevented Tracks to work on ruby 1.8.7)

## Version 2.2

The main change to this release of Tracks is the migration to Rails 3.2. We had
to remove some features because the code and dependencies were not compatible with
Rails 3.2. This may impact your scripts or mobile apps that integrate with
Tracks using SOAP XML API.

Tracks now  includes support for Ruby 1.8.7 and Ruby 1.9. For development, you
need to use Ruby 1.9, version 1.8.7 is not supported by some dependencies for
testing. The next version of Tracks will only support Ruby 1.9. Support for
older versions of Ruby will be droppped.

New and changed features
* Updates to all locales
* Improvements to mobile view
* Drag and drop should work on mobile devices
* The email adres for administrator is now a global setting in site.yml, not an
  attribute in the User model. This means you need to set the admin_email in
  site.yml when you upgrade. (The email address is shown on the signup page)

Removed features
* The outdated code for login in using OpenID has been removed. Also the login
  code for CAS and LDAP has been removed because of compatibility issues with
  Rails 3.2. We plan to migrate to Devise and OmniAuth to get these features back.
* Removed the SOAP XML interface. Please use REST.

New and changed features (technical)
* Improvements to the XML and REST API
* Improvements to the MessageGateway to pass email to Tracks. Since the SOAP
  interface is removed, this is a good way to import an email as a todo.

Under the hood
* Upgrade to Rails 3.2. This means Tracks makes use of the new asset pipeline
  of Rails.
* Uses Cache Digest. This speeds up page rendering a lot
* Migrated to Tolk for managing translations
* Upgraded to JQuery 1.8.3 and JQueryUI 1.9.0

## Version 2.1.3

Upgrade Rails to 2.3.16 to address security vulnerabilities in Rails

## Version 2.1.2

Upgrade Rails to 2.3.15 to address security vulnerabilities in Rails

## Version 2.1.1

Various bugfixes

## Version 2.1

NOTE 1: To use this version you need to migrate your database. Not migrating
will cause new actions not to appear!

NOTE 2: Tracks' source code has moved to a new place on GitHub. Also the wiki
moved to GitHub, see the changed URLs above.

New and changed features:
1. Redesign of the completed todos: a new overview page. Also all context and
   project pages have a link to their completed actions
2. New locales (es, he and fr) and updated locales (de, nl)
3. You can star an action right from the form for adding a new action
4. Redesign of preferences page
5. You can now mark an action complete from the tickler
6. Project names can now contain comma (',') in it name
7. Context view now shows hidden and pending actions
8. Mobile improvements by Tim Madden (we now require some javascript support
   on the mobile)
9. Two extra defer periods in the context menu of an action
10.There is a review page where you can see stalled or neglected projects.
   There is a reviewed button on the project edit page.
11.You need to change your password: migrated to better BCrypt hash algoritm for
   storing passwords by Jan Stępień

New features (technical)
1. There are two example ruby scripts in /doc to use the REST API to add a todo
   or a project template with todos from the command line
2. The tag page can now select actions from mulitple tags using AND and OR.
   There is no gui for this.
   Syntax is /todos/tag/tagA,tagB?and=tagC to select all todos
   with (tagA or tagB) AND tagC

Under the hood:
1. Upgraded rails to 2.3.12, jquery to 1.7.1 and jquery-ui to 1.8.17
2. Fixed several issues with the REST API
3. Upgraded the act_as_statemachine plugin. This change requires a
   migration. See note above!
4. Migated to bundler for gem dependencies
5. Migrated to cucumber and capybara for integration testing
6. Development mode shows a work-in-progress banner on top of the screen

See https://github.com/tracksapp/tracks/compare/v2.0...v2.1 for all detailed
changes. And for those upgrading from 2.1RC1, the changes are here:
https://github.com/tracksapp/tracks/compare/v2.1RC1...v2.1

## Version 2.0

New features:
1. Redesign of menus and introduction of a context menu per todo
2. You can now set the default tags for a project which are added automatically
   to a new todo in that project if no tags are supplied
3. Tracks now includes support of dependencies. Making an action dependent on
   another action will hide it until the dependency is completed
4. You can now drag an action from one context to another
5. Support for entering multiple actions in one form
6. You can now promote an action to a project
7. It is easier to view notes on the mobile interface and other interface fixes
8. The project description supports markup
9. Support for Mail.app (message://) and OneNote (onenote://) links in notes
10. The email receiver is now able to receive email from several email adresses.
    In site.yml this could be set to the previous behavior (receive from one
    address per user)
11. You can enable open signup (like in tracks.tra.in)
12. Cleanup of context page
13. Support for CAS for login
14. Support for adding Tracks as a GMail Widget with instructions on the
    Integrations page
15. Tracks now supports internationalization. First translations are German and
    Dutch. See http://www.getontracks.org/wiki/Translating-Tracks if you'd like
    to help translate Tracks to other languages

Under the hood
1. All js is migrated to jQuery and most ui-widgets are migrated to jQuery-UI
2. Cucumber is added for integration testing. The RSpec stories are migrated to
   cucumber
3. Upgraded to rails 2.3.11 and upgraded most gems/plugins
3. Bugfixes (lots of them)

## Version 1.7

New features:
1. Recurring todos
2. Cleanup of feed page and add feed for starred actions
3. New interface to import an email / sms messages into Tracks (needs an email
   server on the same server as Tracks)
4. New buttons to quickly defer an action 1 or 7 days
5. Calendar view to review due actions, includes iCal feed to use in your
   calendar app (tested with Google Calendar, Evolution, Outlook 2007)
6. You can now sort projects on number of active todos
7. Support for OpenSearch. This means you can add a Tracks as a search provider
   in your webbrowser (tested on FF3 and IE7)

Under the hood:
1. We now allow users again to stay logged in on two devices at the same time
2. Started to move selenium tests to RSpec
3. Upgrade to Rails 2.2.2
4. Move site specific configuration out of environment.rb for easier updating
5. Bugfixes, including fixing OpenID

## Version 1.6
1. Upgrade to rails 2.0.2
2. New mobile interface (with some iPhone compatibility fixes)
3. New search functionality to search on todos, projects, contexts and notes
4. Bugfixes

## Version 1.5
1. Show from date allows you to postpone the appearance of actions in the list
   until you can do something about them (like a 'tickler')
2. Tagging of actions
3. Simple management of users (deleting users through the web interface)
4. Import and export of data in various formats
5. Fantastic RESTful API to provide access to actions via scripts
6. Mobile interface designed for use on mobile phone browsers
7. Improved ease-of-use for installation and upgrading
8. Optional support for authentication via OpenID or LDAP
9. Update to Rails 1.2.3
10. Per-user time zone preference
11. Use autocomplete fields for Project and Context specification to support
    on-the-fly adding of each
12. Add a "Hidden" status to projects
13. Add optional Default Context for a Project
14. Add ability to sort projects alphabetically
15. Add "starring" of actions
16. Statistics page with graphs
17. Rake task to set password. Usage: rake tracks:password USER=useranme

## Version 1.041

### New features

1. Tracks now has an API, written by Luke Melia, which allows you to create new actions in a particular context remotely, using scripts. See http://www.rousette.org.uk/projects/downloads/comments/adding-next-actions-via-scripts-the-tracks-api/ for some example scripts and instructions. If anyone creates scripts for other platforms (Windows or Linux), or more fancy ones for Mac OS X, do share them!
2. The feeds page now lists iCal links alongside each RSS and TXT feed link. Copying your chosen link and pasting it in to the text box that appears in iCal when you choose Calendar > Subscribe.. Name your calendar as you wish, but make sure that you get it to refresh periodically and that the 'Remove Todo items' checkbox is UNCHECKED (obviously ;-) ). Then your Tracks next actions should appear as todo items in iCal, with proper due dates assigned, and notes in the notes field. The todos should update periodically in iCal as you add, delete or complete items in Tracks, but the subscription is read-only from iCal's end. However, it does allow you read access on the move if you sync iCal with your Palm or mobile phone.
3. Setting no_completed in the user preferences to zero now removes the completed items box completely from the home page and from the individual context and project pages, if you don't like completed items cluttering those pages up.
4. You can set a local time zone in environment.rb if your local time zone is different from the time zone setting on the server running Tracks.
5. 'Add users' link added to the navigation bar for the admin user, which is a convenient way to get to the signup page.
6. Luke fixed the edit actions method so that changing an action's context immediately moves it in an Ajaxy way to the new context.
7. Updated vendor directory to Rails 1.1

### Minor additions and bug fixes

1. Deleting a context now correctly deletes any actions in it as it should. Again.
2. The user's context ordering is now honoured in the feeds (Luke Melia).
3. A 'spinner' next to the date at the top of the page informs you that an Ajax action is in progress (Luke Melia).
4. Text feeds now don't have superfluous blank lines.
5. Fixed errors on 'done' page.
6. Expansion and collapsing of the context boxes now works without a refresh after an Ajax action. (Luke Melia).
7. User id only is now stored in the session object, reducing the size of the object and improving security (Luke Melia).
8. Notes page now doesn't raise an error if you don't have any notes created yet.
9. notes.yml fixture fixed so that it contains all the correct fields, so using the test contents should work properly again.
10. The Completed Items box on the home, context and project pages now shows the same format for the actions as the Done page.
11. The navigation bar now shows which page you are on by underlining the appropriate link and colouring the text black.
12. There are new accesskeys for the notes page (alt/ctrl o) and user preferences (alt/ctrl u).

## Version 1.04

1. Tidied up the interface a bit, fixing mistakes in the wording.
2. The number of actions reported is now correctly pluralized depending on the number of actions (e.g. 1 action, 2 actions).
3. Added a Note model and notes database table. Notes have their own interface (/notes lists them all, and /note/1 shows note id 1), but they are displayed on the /project/show/[name] page. For now, notes belong to a particular project, and are added from the /project/show/[name] pages. You can delete and edit notes either from the /notes page or from the /note/[id] page. Notes use Textile/Markdown formatting.
4. Can now host multiple users on a single tracks install. User creation only possible by admin user.
5. Major improves to the render-flow, code reuse and MVC rationalisation.
6. Rails based db creation and migration via rake.
7. Added loginhash to settings.yml.
8. Modify signup to prevent is_admin being set by malicious user. Begin work on standardising layout for login controller.
9. BIGGEST NEW FEATURE: Tracks is now properly multi-user, thanks to the work of Nicholas Lee. Any new users that you sign up can't view any of your next actions, contexts, projects or notes, and they get a clean slate to add their own. Great Things are planned in this direction...
10. Projects now have a description field which you can edit in the form on [tracks_url]/projects. It's optional, but you can use it to remind you of the aims or purpose of the project. If you have a description, it's displayed in italics just under the project name.
11. Included a new rake task. Call it with `rake setup_tracks` at the command line. This automates a lot of the work of setting up tracks, like renaming the template files (*.tmpl). However, you need to make sure that you've copied database.yml.tmpl to database.yml before you run it (and added the correct settings to the file), because rake can't run without that file in place. The task is safe to run if you're upgrading, because it ignores already converted files.
12. Changed the shebang lines to `#!/usr/bin/env ruby`. This should work for all \*nix based setups (Linux or Mac OS X), but Windows users will probably have to change it. Try this command at the command line, run inside the Tracks directory:
    ```ruby -i.bak -pe 'gsub!("#!/usr/bin/env ruby", "#!c:/ruby/bin/ruby")' public/dispatch.* script/*```
13. The TXT view is now sorted by position, just as the home page is.
14. *Contributed by lolindrath:* Items that are overdue are coloured red, and have the text 'Overdue by X days' in the badge. Other due dates are given as days from now (up to a week away in orange, more than a week away in green), and the tool tip shows the actual date.
15. Projects and Contexts in [tracks_url]/projects and [tracks_url]/contexts can now be rearranged in order by dragging and dropping. Just pick the item up by the 'DRAG' label and drop it where you want.
16. Got rid of the 'fresh actions' box on the home page. When you create a new action, it is now automatically inserted (via the magic of Ajax and RJS templates) at the bottom of the correct context box.
17. The next action count badge is now dynamically updated whenever you add or delete a next action, so that you don't have to refresh to see the count updated.
18. Validation errors are now reported in a status box (just above the new next action form).
19. There's a rake task (upgrade_sqlite_db) which allows you to safely upgrade databases created with version 1.03, afterwhich you can run rake migrate to complete the process. From there, rake migrate should work OK.
20. Moved settings for Tracks from the file settings.yml to the database. Running `rake migrate` will update your database appropriately, and add the default settings into it. Then you should be able to visit `http://0.0.0.0:3000/user/preferences` to view and edit your settings. The advantage is that you don't need to mess about with the settings.yml file, and each of the users can have their own settings.
21. Session data is now stored in the database rather than a file in tracks/tmp. This should prevent the tmp directory cluttering up the file system, and give better performance. You need to run rake migrate to add the session table to your database.
22. You can now change the password for the logged in user (user/preferences)
23. Lots of new text and RSS feeds added by Luke Melia. These are accessed via the feed icon on in the main navigation.

## Version 1.03

1. Added back border="0" to images which I had mistakenly taken out. This should fix the ugly red border around images that appears in Firefox (thanks, Adam Hughes).
2. Removed the section in `config/environment.rb` which requires Redcloth. This was causing errors because Rails now requires Redcloth itself. This means that you now need to have Redcloth installed as a gem (gem install redcloth) (thanks, Jim).
3. SQL dumps are now available for each of the available database formats (MySQL, PostgreSQL and SQLite), as well as a separate file containing some example contents, which should work for all of the formats. These are in the `tracks/db` directory (thanks, Jim)
4. The new item forms on all pages now use a mini calendar which pops up when you click in the due date field. The calendar is the GPL one from dynarch.com http://www.dynarch.com/projects/calendar/
5. *Contributed by Lolindrath:* Toggling of contexts in on the home page to collapse or expand their display via a small '+' or '-' graphic. This is independent of the shown/hidden setting for contexts, and is ideal for just hiding things on the fly to focus your view.
6. *Contributed by Jim Ray:* Jim added a host of fixes and bits of cleaning up, including a position column for contexts and projects to allow custom sorting, and changes to the links for pages to make them more human-readable.
7. *Contributed by Nicholas Lee:* URLs are now generated using the `url_for` or `link_to` methods, which should mean that people using Tracks in a subdirectory won't have to manually tinker with the URLs to get them to work.
8. *Contributed by Arnaud Limbourg, ticket 18:* A new entry in settings.yml allows you to choose the number of completed actions you want to see on the home page. Also sorts by due date (ascending) first, then creation date (descending) on the home page, `/context/show/[name]`, and `/project/show/[name]`.
9. Counts of next actions are now shown on the `/context/show/[name]` and `/project/show/[name]` pages. These just show how many uncompleted actions you have in the selected context or project.
10. *Patch by lolindrath:* Sorting by date is now much smarter on the home page. Actions are sorted by ascending due date then ascending creation date, but non-due dated items sort to the bottom. This means that the most urgent items float to the top of each context list.
11. You can now uncheck actions from the completed actions list, so that they dynamically appear back in the uncompleted actions area.
12. A tiny improvement: the toggling of the individual notes now uses Element.toggle from prototype.js, so it doesn't have to be an onLoad property of the body tag. This means that you don't get the notes flashing before they are hidden when you load or reload a page.
13. All the adding, updating, deleting and marking actions done is performed using Ajax, so happens without needing to refresh the page.
14. There's a new setting in settings.yml ('staleness_starts') which defines the number of days before which actions get marked as stale. Let's say you set it to 7 days. Actions created between 7 and 14 days ago get marked pale yellow, those created between 14 and 28 days ago (staleness_starts x 2) get marked darker yellow, and those created more than 28 days ago (staleness_starts x 3) are fluorescent yellow! This is only applied to items without a due date, so you can add items to be done some time in the future without getting yellow splashed all over the place (thanks to Nicholas for the patch to restrict to items with no due date).
15. Contexts and projects can now be sorted in any order you like. Arrow buttons on the `/contexts` and `/projects` pages let you move an item to the top, up, down or to the bottom. For contexts, this affects the order in which they sort on the home page. Position is also used to sort the listings of active/completed/hidden contexts and projects in the 'sidebar', and in the dropdown lists on forms.
16. You can mark projects as completed (by editing the project on `/projects`). In the 'sidebar' active and completed projects are shown separately, but you can still view the completed project.
17. New images (from eclipse.org) for the edit, delete, notes and up, down, top and bottom buttons. I've made a greyscale version for the default, then the coloured version gets loaded when the mouse is hovering over the button.

## Version 1.02

1. Uses Rails 0.10.0
2. Added validation for the entry fields. If you enter a bit of text that's too long or you omit the description (not much point in a blank next action!) you'll get an error message and the action won't be saved.
3. Added action caching.
4. Did a bit of refactoring to try to make page loading a bit more efficient.
5. Added a new row to the context table: 'hide'. This determines whether a particular context gets hidden on the main page. If the checkbox on the add new context form is checked, the context is hidden, and isn't listed on the front (todo/list) page. This is useful for contexts like 'wish list' or 'someday/maybe' that you don't want taking up your attention all the time.
6. Added a list of links to the hidden contexts at the bottom of the page.
7. Changed the method of adding due dates to drop-down option lists. It's more obvious and less error prone than typing in the date. Your preferences for date formatting are still honoured when displaying due dates.
8. Added a favicon, kindly produced by Jim Ray.
9. Added border="0" to the button images to stop Firefox putting a red border around them.
10. Added a new path:, base: setting in settings.yml. This is used in constructing URLs in standard.rhtml and other places for the javascripts and stylesheets. You need to specify it in the format `http://my.domain.tld/subdir/tracks`, or whatever the full URL is. This should help people who put Tracks in a subdirectory.
11. Added some rudimentary sorting of completed items. They are now sorted in to done today, done in the last 7 days and done in the last 31 days. At the bottom of completed.rhtml, there's a link to completed_archive.rhtml, which shows archived items older than 31 days.
12. Changed the method of generating links to stylesheet and javascripts. Together with the new Routes, this should sort out any problems with putting Tracks in a sub-directory.
13. config/environment.rb now checks to see if a gem version of Redcloth is installed that is greater than version 3.0.3. If that fails, it falls back on the packaged lib version. Note that there's an odd bug I can't seem to pin down that means that if you are using the packaged lib version, you'll get some errors like: `./script/../config/..//lib/redcloth.rb:169: warning: already initialized constant VERSION` or `./script/../config/..//lib/redcloth.rb:170: warning: already initialized constant DEFAULT_RULES` but ONLY if you're using the development environment; with production it's fine, and with the gem version of Redcloth it's fine in both environments.
13. Modified the 'count' badge on todo/list: now shows the number of uncompleted items in contexts that *aren't* hidden (i.e. the actions actually listed on todo/list). Number of items in hidden contexts are shown in parentheses after the link to that context. So you don't forget about that stuff ;-)
14. Protected RSS and text feeds at last! The appropriate URLs can be copied from the RSS and TXT links in the navigation bar. The URL includes the login name of the current user, and an MD5 encoded string of the 'word' field of the users table. This is checked against users to make sure it's valid; if it is, the feed is displayed, if not, you get an error message.
15. Better signup system implemented. The users table has another new column, 'is_admin'. If no users have been created, the first user to sign in is made the admin user. If the admin user (while logged in), visits the signup page, the form indicates that this user can create a new user (who won't have admin rights). If anyone who is not not logged in and not an admin user visits signup, they are greeted with a message that they don't have permission to create an account, and should contact the admin. I've made a new field in settings.yml to hold your admin email address for this purpose. This should mean that you can safely leave signup.rhtml intact on a public server.
16. Added a list of other contexts and projects to the context/show/[id] and project/show/[id] pages, so that you can easily navigate between the filtered views of contexts and projects, without having to go back to context/list or project/list.

## Version 1.01

A small increment to fix a few bugs and typographical errors in the README:

1. README.txt now lists the correct location for the dump file
2. Fixed the redirection from the login page. Once you have signed up or logged in, you should be taken automatically to the main todo/list page. This also works once you have logged out and clicked the "<< login" page to get back to `login/login`. (Thanks, Max Prophet!)
3. Properly updated for Rails 0.9.3: this probably means that it won't work for a lower version of Rails. If you have the gems version of Rails installed, you can update it with: `sudo gem update rails`
4. Made some minor changes to the appearance of the listed items, so that the description wraps properly, and the tool buttons (edit, delete and notes) are always in the same place relative to the checkbox.

## Version 1.0

1. Updated to run on Rails 0.9.1. This should work with any 0.9.x branch.
2. Added a proper edit page for todos. This also allows you to add a todo to a project, or re-assign it to a new project.
3. Improved the efficiency of the Projects page: it now only finds the Project you've selected, rather than all of them (thanks, Johan http://theexciter.com/!)
4. You now get a warning if you try to delete a project or context with undone items. If you choose to continue, the dependent items will be deleted, so that the list page should no longer break.
5. Using Redcloth for markup now that it allows you to use either Textile or Markdown format transparently. This is now included in the distribution, so that you don't need to install it.
6. Added links to context/list page so that you can go directly to `todo/show/blah` if you click the link for context 'blah'.
7. You can now set the date format you want to use in the file config/settings.yml. Use the strftime formats, with whatever separator you like. e.g. If you want 2004-12-31, the correct format is `%Y-%m-%d`. 31/12/2004 would be `%d/%m/%Y`. The same format is used for entry of the date in the due date box, and for display of the date in the list.
8. You can now add a new item to a particular project when you are viewing it at `/project/show/[id]`. This makes it easy to add a block of next actions to a project. Edit and delete buttons work on this page, but redirect you to `/todo/list`. I need to fix this.
9. Added a login system by using the login_generator: http://wiki.rubyonrails.com/rails/show/LoginGenerator. The first time you access the system, you need to visit `[tracks_url]/login/signup` to enter a username and password. Then when you visit, you will be greeted with a login page. This stores a temporary cookie for your session. The whole app is protected by the login.
10. You can now add a new item to a particular context when you are viewing it at `/context/show/[id]`. This makes it easy to add a block of next actions to a project. Edit and delete buttons work on this page, but redirect you to `/todo/list`. I need to fix this.
11. Feeds! There's an RSS feed available at `[tracks_url]/feed/na_feed` which shows the last 15 next actions, and a text feed at `[tracks_url]/feed/na_text` which gives you a plain text list of all your next actions, sorted by context. You can use the latter to display your next actions on the desktop with GeekTool. Simply set up a shell command containing the following: `curl http://[tracks_url]/feed/na_text`. Obviously, you need to replace [tracks_url] with the actual URL to the Tracks application.
