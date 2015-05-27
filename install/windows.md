---
title: Install to Windows
layout: en
---

# Install to Windows

This document describes how to install PGroonga to Windows.

## Supported versions

You can use both 32bit version Windows and 64bit version Windows. You can use any Windows that are supported by PostgreSQL.

## How to install

Install PostgreSQL {{ site.windows_postgresql_version }}. You can choose [installer version](http://www.enterprisedb.com/products-services-training/pgdownload) or [zip version](http://www.enterprisedb.com/products-services-training/pgbindownload).

Download PGroonga package:

  * [32bit version](http://packages.groonga.org/windows/pgroonga/pgroonga-{{ site.pgroonga_version }}-postgresql-{{ site.windows_postgresql_version }}-x86.zip)
  * [64bit version](http://packages.groonga.org/windows/pgroonga/pgroonga-{{ site.pgroonga_version }}-postgresql-{{ site.windows_postgresql_version }}-x64.zip)

Extract the downloaded PGroonga package. You need to specify PostgreSQL folder as extract target folder.

If you installed installer version PostgreSQL, `C:\Program Files\PostgreSQL\9.4` is the extract target folder.

If you installed zip version PostgreSQL, `%POSTGRESQL_ZIP_EXTRACTED_FOLDER%\pgsql` is the extract target folder.

Create a database:

```text
postgres=# CREATE DATABASE pgroonga_test;
```

(Normally, you should create a user for `pgroonga_test` database and use the user.)

Connect to the created database and execute `CREATE EXTENSION pgroonga`:

```text
postgres=# \c pgroonga_test
pgroonga_test=# CREATE EXTENSION pgroonga;
```

That's all!

Try [tutorial](../tutorial/). You can understand more about PGroonga.