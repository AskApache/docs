---
title: database:update
level: intermediate
---
database:update
===============

Nut's `database:update` command repairs and/or updates the database.

## Usage

```bash
    php ./bin/console database:update
```


## Example

### Creation of ContentType table

```bash
$ php ./bin/console database:update
Modifications made to the database:
 - Created table `bolt_entries`.
Your database is now up to date.

```
