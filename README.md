# KIM Admin
Manage your KIM (keep in mind) list for fanlistings.

## Disclaimer
By using this script, you agree I, Tess, am NOT responsible for any errors that may occur on your site. I created KIM Admin as a way for people to easily manage a KIM script (and a secure one at that!) and not to deliberately cause you headaches. You agree that by using this, you will not distribute it under your name and/or claim as your own. You also agree not to distribute it -- even with credit -- without my written consent.

The credit link on the forms and members list can be removed, as long as you abide by the above rules, and the rules of the GPL3 license.

## Requirements
I have tested KIM Admin under the following versions of PHP and Mysql. KIM Admin was also tested under the Mysqli and PDO drivers.

**PHP** 
* 5.2.6,
* 5.2.8
* 5.3+
* 5.4

**MySQL**
* 5.0.51b
* 5.1.30
* 5.1.33
* 5.3

## Features and Documentation
### Version 1.0 (Beta)
* The ability to pull fanlistings from another table (via a fanlisting script, for example) or use KIM Admin's built-in functioning for adding listings to the script.
* Multiple fanlistings per email.
* Approval (for adding/updating) and Update (for editing information straight from the admin panel) email option.
* Member Functions
  * Personal or 12-character generated password.
  * Password reset.
  * Search for listings and emails in the admin panel.
  * Option of a bulleted list, dropdown menu, or all members display.
  * Pagination for all options.
* Anti-SPAM functioning for the forms.
  * Akismet, an external service; optional.
  * JavaScript "cheat" that adds a field through JavaScript code that triggers an error should the user (or bot) not use JavaScript; optional.
  * Filtering of "bad words" and "bots" from the forms; until version 1.2, this list could not be edited.
* Options
  * Statistics template (for show-stats.php).
  * HTML Mark-Up choice (XHTML or HTML).

### Version 1.0
* E-mail Functioning
  * E-mail templates were added to options table.
  * Each member can be e-mailed individually, or as a group.
* Member Functioning
  * "Add Member" option added to members.php.
  * "Previous Owner" field added to the members table.
  * "Send me my details!" option for the join form; this option can allow members to choose whether their details are e-mailed to them when the form submits.
* Miscellany
  * Instead of adding one listing at a time, you can now choose up to 10 listings to be added at the same time.
  * BellaBuffs conversion file was added: <bellabuffs-convert.php>
  * New search form in members.php; searchable by e-mail.

### Version 1.1
* Members Functioning
  * An 'update' field was added to the members table; this is for ensuring we know whether the member has joined or simply updated their information.
* Miscellany
  * Five templates added: three templates for the members list (the header, footer, and body templates) and two e-mail templates for approving and updating members.
  * Multipling approving, updating and rejecting added to members.php.
* Bugfixes
  * Pagination fix for <show-members.php>
  * A couple of tweaks and fixes to <func.inc.php>
  * The <values.php> file was renamed to <listings.php>, and will be deleted when upgrading.
  * SPAM protection tweaked; the script now checks for bbCode in the form and only has *one* JavaScript field, if enabled.

## Installation
Follow the instructions below to install the script.

* Download KIM Admin (which, if you're viewing this file on your computer, you've already done), and unzip the .zip file into a folder name of your choice. For example's sake, we're unzipping into a folder named "kimadmin".
* Go to the rats.inc.php file -- located in the "1.2" folder in your "kimadmin" folder -- and edit the variables the file tells you to edit. There's a "STOP RIGHT HERE" note when the editing process ends in the file, so you need only edit the database variable; the table prefix and database engine variables are optional.
* > Many people have complained of the database not connecting despite their details being correct; this is, nine times out of ten, due to the database engine you've chosen. If you've chosen 'mysqli' or 'pdo', then select the 'mysql' engine, and your database problems should go away. :')
* Once edited, upload all the files in your folder onto your site through your FTP program of choice. I'd recommend you upload these to subfolder.
* > Example: http://yoursite.com/kim_admin_folder/
* The /example folder does not need to be uploaded, though it has a required file (fig.inc.php) in the folder, as well as code snippets for you to take examples from.
* Once uploaded, run install.php in a browser of your choice.
* > Example: http://yoursite.com/kim_admin_folder/install.php
* Before running the script, once again, make sure all the variables in your config file are set correctly. Run it, and an success message should appear. Once the installation finishes, delete the file from your server immediately! This is EXTREMELY important. Should you forget to delete the file, the script will exit and display an error message until you delete the file from your server.
