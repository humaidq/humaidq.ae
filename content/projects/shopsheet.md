---
title: ShopSheet
GitURL: shopsheet
MailingList: general
Section: "Web Applications"
License: AGPL-3.0-only
Language: Go
date: 2019-06-30
GoDoc: true
LatestVersion: v0.1
HasBuilds: true
Description: "An instant ecommerce website generator based on a spreadsheet file."
Usability: 3
---

### 1. Description

ShopSheet is a web app written in Go that converts a spreadsheet file
into an ecommerce website instantly.  

This web app is developed by me and [Akilan Selvacoumar](https://akilan.io)
as a challenge, we ended up implementing a working app in six hours.  

We chose this idea to tackle as a challenge because it solves a problem,
most people know how to use and are familiar with using spreadsheets, so why not build
an ecommerce website generator based on spreadsheets?

### 2. Requirements

The following packages must be installed on your system.

- Go *(tested with 1.12)*
- Git
- LibreOffice *(program uses `soffice` to convert spreadsheets to csv files)*

### 3. Copying and contributing

This program is written by Humaid AlQassimi and Akilan Selvacoumar,
and is distributed under the AGPL 3.0 license.  

### 4. Download and install

```sh
$ go get -u git.sr.ht/~humaid/shopsheet
$ go install git.sr.ht/~humaid/shopsheet
```

### 5. Usage

Run with `go run main.go`.

### 6. Change log

- v0.1 *(Jun 30 2019)*
  - Initial release

### 7. To-do

- [ ] Deploy to Heroku
- [ ] Use [X]ORM
- [ ] Template changes/fixes
  - [ ] Clear cart when changing sites
  - [ ] Allow custom templates
  - [ ] Show add to cart confirmation
