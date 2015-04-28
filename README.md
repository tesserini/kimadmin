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

1.) Download KIM Admin (which, if you're viewing this file on your computer, you've already done), and unzip the .zip file into a folder name of your choice. For example's sake, we're unzipping into a folder named "kimadmin".

Go to the rats.inc.php file -- located in the "1.2" folder in your "kimadmin" folder -- and edit the variables the file tells you to edit. There's a "STOP RIGHT HERE" note when the editing process ends in the file, so you need only edit the database variable; the table prefix and database engine variables are optional.

> Many people have complained of the database not connecting despite their details being correct; this is, nine times out of ten, due to the database engine you've chosen. If you've chosen 'mysqli' or 'pdo', then select the 'mysql' engine, and your database problems should go away. :')

2.) Once edited, upload all the files in your folder onto your site through your FTP program of choice. I'd recommend you upload these to subfolder.

> Example: http://yoursite.com/kim_admin_folder/

The /example folder does not need to be uploaded, though it has a required file (fig.inc.php) in the folder, as well as code snippets for you to take examples from.

3.) Once uploaded, run install.php in a browser of your choice.

> Example: http://yoursite.com/kim_admin_folder/install.php

4.) Before running the script, once again, make sure all the variables in your config file are set correctly. Run it, and an success message should appear. Once the installation finishes, delete the file from your server immediately! This is EXTREMELY important. Should you forget to delete the file, the script will exit and display an error message until you delete the file from your server.

## How-To's and FAQ
> How do I use NL-CovertToPHP or something like it?

When using NL-CovertToPHP, you can include the display code (found in <displaycodes.php>) in any normal query string. For instance, let's say you want it included in a page like collective.php?kim; any normal query string would look like:

```
if(isset($_SERVER['QUERY_STRING']) && $_SERVER['QUERY_STRING'] == 'kim') {
 // code here
}
```
 
Simply change that to:
 
```
if(isset($_SERVER['QUERY_STRING']) && subtr_count($_SERVER['QUERY_STRING'], 'kim')) {
 // code here
}
```
 
...and so on!

> I want to have PHP pages like NL-ConvertToPHP, but I'd like to have the query form as collective.php?page=kim. Is this possible?

It sure is! This is a little more tricker, but if you follow along, it'll be easy to implement in no time! If you'd like a page named, say, 'join', it's something as easy as:

``` 
if(isset($_GET['page']) && $_GET['page'] == 'join') {
 // code here 
}
```

Please note the use of `$_GET` instead of `$_SERVER['QUERY_STRING']`, like above. Since we are specially going after a named query, we don't need thee use of the sever's query string. In fact, if we're looking for specific query strings -- such as 
<collective.php?section=kim> for an example -- we should go with the use of `$_GET` at all times. Using `$_GET` let's the server know we're looking for the specific query string of 'page' in the URL, and should the query match, our page will display!

For more information on query strings, better security measures for query strings, and more examples, please visit <http://liebenkode.in/articles/querystrings/>

> How do I change the look of my members list in show_members.php?

You can change the look of your members list by going into <options.php> in your admin panel, going to the 'Templates' subpage located on the left, and editing your templates there. There is currently -- as of version 1.2 -- a template for the header, footer, and body of your members list. 

For example, let's say you want to display your members in a table. The header template would look something like this:

```
<table class="membersList">
<thead><tr>
 <th>Name</th>
 <th>Details</th>
 <th>Listing</th>
</tr></thead>
```

Your body would look something like this:

```
<tbody><tr>
 <td>{name}</td>
 <td>{email}{text:@} / {url}</td>
 <td>{listing}</td>
</tr></tbody>
```

And your footer would look like this:

```
</table>
```

## Customisation
Once you've installed the script, there's finally the includes. With the .zip file came a folder named "example", which is NOT required to upload, but holds example pages. It also gives you a feel of what the front-end will look like. This is what an include will look like:

```
<?php
 require("fig.inc.php");
 require(KAPATH . "show-join.php");
?>
```

The pages that can be included are: <show-join.php>, <show-members.php>, <show-update.php>, <show-stats.php>, <show-reset.php>, and <fig.inc.php>

> The fig.inc.php file included in /example is REQUIRED to include any of listed files. To find all code snippets of them, go to codes.php in your admin panel. 

You can customise the script through CSS using these classes and IDs that are already defined.

### #show-join, #show-update
> DIV id in show-join.php and show-update.php, in which you can apply any special form or paragraph styles to these particular pages only. Example:

```
#show-join input, 
#show-update input, 
#show-update textarea {
 border: 1px solid #DDD;
 font: 11pt Arial, "Trebuchet MS", Tahoma, Verdana, sans-serif;
 padding: 0.5% 1%;
}

#show-join p {
 line-height: 19pt;
 margin: 0 0 5px 0;
}
```

...and so on!

> To edit your statistics look, go to options.php in your Admin Panel.

## Credits
- In the previous versions of KIM Admin, a lot of the SPAM measures were taken as ideas from Jem's free mail form: <http://jemsmailform.com/> Most of the measures have since been altered -- especially the use of 'bad' words and SPAM bots -- as well as new measures not seen in Jem's form (such as the math problem, and my own preg_match() functions for e-mail and URL checks). The point system included in version 1.2 is from an earlier version of my script Listing Admin and *not* from Jem's current version of the mail form.

- All that being said, many, many thanks to Jem for being the amazing PHP developer that she is -- she is one of three people that inspire me to take such cautious (if abundant on my part!) measures in security and form checking. The script land would truly be a wonderful place if developers were more like Jem; thank you so much, Jem! :'))))
 
- MicroAkismet <http://vanhegan.net/software/akismet/>

## Special Mention
If you find you're unsatisfied with KIM Admin, and you're using Enthusiast as a fanlisting script (much less phpFan itself), I'd recommend using the phpFan add-on for KIM found here: <http://scripts.ishallnotcare.org/phpfan-add-ons/> As of the current version, it only caters to users with Enthusiast, though it's been mentioned this will change in the future.
