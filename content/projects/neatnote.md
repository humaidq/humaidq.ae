---
title: Neat Note
GitURL: neatnote
MailingList: general
section: "Web Applications"
License: AGPL-3.0-only
Language: Go
date: 2019-12-29
GoDoc: true
HasBuilds: true
IssueTracker: true
Description: "A Lobsters-like web app for university students to post notes and question."
LatestVersion: v0.3.3
Usability: 4
---
### 1. Description

This is a web app which allows students to share their lecture notes, helpful
resources, start discussions, or ask questions. This site is separated into
different sections for different courses.

Users are authenticated by emailing the users a one-time password to their
university email address, which also confirms that they are either students or
faculty of that university.

Markdown, HTML, and LaTeX are supported in comments and posts, so students are
able to write notes in any way they are comfortable with. [goldmark] is used
for rendering Markdown, and [bluemonday] sanitizes the output which includes
user added HTML. LaTeX is rendered using [MathJax] on the client side.

Users are able to upvote posts, and posts with more upvotes (called iota), will
appear on top. This is somewhat similar to upvoting in Hacker News or Reddit,
which many are familiar with.

### 2. Requirements

The following packages must be installed on your system.

- Go *(tested with 1.13)*
- Git
- GNU Make

### 3. Copying and contributing

This program is written by Humaid AlQassimi, and is distributed under the
AGPL 3.0 only license. This means if you make your
own fork of this app, you must release its source to its users under the
same license.

### 4. Downloading and running

```sh
$ git clone https://git.sr.ht/~humaid/neatnote
$ cd neatnote
$ make
```

### 5. Setup & Usage
Running the web server will automatically generate a configuration file
(`config.toml`) if it is not yet created.
```sh
$ ./neatnote run
```
The program will exit when run for the first time, prompting you to configure
the program. Check out the [configuration documentation](https://godoc.org/git.sr.ht/~humaid/neatnote/modules/settings#DatabaseConfiguration).

If you are using the MySQL driver you must create a table with the same name as
the user. You will have to also add the `session` table:

```sql
CREATE TABLE `session` (
    `key`       CHAR(16) NOT NULL,
    `data`      BLOB,
    `expiry`    INT(11) UNSIGNED NOT NULL,
    PRIMARY KEY (`key`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

You should then run the web server again, and login with your account. You can
set your account as admin by running the following command:
```sh
$ ./neatnote set-admin admin@example.com
```

You may revoke the admin status by using the `--status false` flag.

The last thing to do is to add the courses needed on the web interface, using
the admin account.

### 6. Change log

- v0.3.3 *(Feb 10 2020)*
	- Fixes [a security issue](https://lists.sr.ht/~humaid/general/%3C20200210185437.338764ef%40serow%3E).
- v0.3.2 *(Jan 13 2020)*
	- Nicely format blockquotes and code blocks.
	- Make badge radio button labels clickable in the profile.
	- Fix issues with transparent images in dark mode and large images in
	  mobile view.
- v0.3.1 *(Jan 12 2020)*
	- Rename login validation to verification.
	- Show badges in the registered users listing in admin dashboard.
	- Show comments in request data, and hide empty fields.
- v0.3 *(Jan 12 2020)*
	- Add an admin dashboard, with option to suspend and view users.
	- Add lite/print page for posts.
	- Mobile friendlyness and dark theme improvements.
	- Redirect for mismatching post/course ID.
	- Other styling tweaks.
	- Other templating and routing improvements.
- v0.2 *(Jan 11 2020)*
	- Revamp design to be more modern.
	- Moved access control and context initialisation to middlewares to reduce
		code duplication.
	- Other improvements and bug fixes.
- v0.1.1 *(Jan 10 2020)*
	- Fixed bug where posts don't load for non-logged in users.
- v0.1.0 *(Jan 9 2020)*
	- Initial release.
	- Has basic features such as:
		- Authentication.
		- Posting, editing posts and comments.
		- Deleting posts and comments (admin).
		- Voting and sorting.
		- Badges, display names, anonymous posting.

[goldmark]: https://github.com/yuin/goldmark
[bluemonday]: https://github.com/microcosm-cc/bluemonday
[MathJax]: https://www.mathjax.org/
