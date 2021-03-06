---
title: GRANT USAGE ON SCHEME pgroonga
layout: en
---

# `GRANT USAGE ON SCHEME pgroonga`

PGroonga defines functions, operators, operator classes and so on into `pgroonga` schema. Only superuser can use features in `pgroonga` schema by default. Superuser needs to grant `USAGE` privilege on `pgroonga` schema to normal users who want to use PGroonga.

This document describes how to grant `USAGE` privilege on `pgroonga` schema to a normal user.

## Create a normal user {#create-user}

First, create a normal user `alice` by [`CREATE USER`](http://www.postgresql.org/docs/{{ site.postgresql_short_version }}/static/sql-createuser.html):

```sql
CREATE USER alice;
```

Normal user `alice` can't access any objects in `pgroonga` schema at this time. For example, `alice` can't use [`pgroonga.snippet_html` function](functions/pgroonga-snippet-html.html):

```sql
SELECT pgroonga.snippet_html('PGroonga is fast', Array['fast']);
-- ERROR:  permission denied for schema pgroonga
-- LINE 1: SELECT pgroonga.snippet_html('PGroonga is fast', Array['fast...
--                ^
```

You need to grant `USAGE` privilege on `pgroonga` schema to `alice`.

## Grant `USAGE` privilege on `pgroonga` schema {#grant}

You can grant `USAGE` privilege on `pgroonga` schema to normal user `alice` by [`GRANT`](http://www.postgresql.org/docs/{{ site.postgresql_short_version }}/static/sql-grant.html):

```sql
GRANT USAGE ON SCHEMA pgroonga TO alice;
```

Now, `alice` can use all features in `pgroonga` schema. For example, `alice` can use `pgroonga.snippet_html` function:

```sql
SELECT pgroonga.snippet_html('PGroonga is fast', Array['fast']);
--                     snippet_html                     
-- -----------------------------------------------------
--  {"PGroonga is <span class=\"keyword\">fast</span>"}
-- (1 row)
```
