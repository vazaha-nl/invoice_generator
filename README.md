## Invoice generator

### Introduction

For my business I need to send out invoices that are mostly based on my time registration data. The first few times I did it by hand using an xls export, but that got old real fast, so, being a developer, I took some time to automate it. After a while I thought it might be fun to open source this. Because why not?

### What it does

This Laravel based app retrieves all data from my time tracking app [Toggl Track](https://toggl.com/track/) using their [REST api](https://developers.track.toggl.com/) and compiles it into the correct form to create an invoice for [e-boekhouden](https://www.e-boekhouden.nl/) using their [SOAP webservice](https://www.e-boekhouden.nl/koppelingen/api). 

It creates invoice lines based on time entries grouped by project name. The time will be rounded to nearest quarters. The line description will include the project name and a list of dates, intelligently generated.

### Audience

This app is of very limited use to others. It works for me but it is by no means finished nor stable. The implementation is very specific. And there is only a very crude CLI interface. And no documentation except this readme. 

But if you're using Toggl Track for time tracking and e-boekhouden for book keeping, and you have a very similar work flow and invoices as I have, and you're feeling brave, this just might be useful to you. 

### Requirements

- PHP8.1+
- a relational database like mysql
- a "Toggl Track" account
- an "e-boekhouden" account

### Installation

- Clone the repo
- `composer install`
- Copy  `.env.example` to `.env` 
- `php artisan key:generate`
- Adjust `.env` settings, in particular the `DB_*`, `TOGGL_TRACK_*` and `E_BOEKHOUDEN_*` keys

### Usage

Run `php artisan invoice:generate` and follow the prompts. 
