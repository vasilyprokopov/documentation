---
title: Strapi 5 uses koa-body v6
description: Strapi 5 uses koa-body v6, which updates node formidable to v2.
sidebar_label: koa-body v6 and formidable v2
displayed_sidebar: devDocsMigrationV5Sidebar
tags:
 - breaking changes
 - body middleware
 - dependencies
 - ctx
 - upgrade to Strapi 5
---

import Intro from '/docs/snippets/breaking-change-page-intro.md'
import MigrationIntro from '/docs/snippets/breaking-change-page-migration-intro.md'
import YesPlugins from '/docs/snippets/breaking-change-affecting-plugins.md'
import NoCodemods from '/docs/snippets/breaking-change-not-handled-by-codemod.md'

# Strapi 5 uses `koa-body` v6

Strapi 5 uses [`koa-body`](https://github.com/koajs/koa-body) v6, which updates `formidable` to v2. This means uploaded files have new properties.

 <Intro />

<YesPlugins />
<NoCodemods />

## Breaking change description

<SideBySideContainer>

<SideBySideColumn>

**In Strapi v4**

A user might create custom endpoints and handle files with the `ctx` object:

  ```js
  const endpoint = (ctx) => {
      ctx.request.files.fileName.path
      ctx.request.files.fileName.name
      ctx.request.files.fileName.type
  }
  ```

</SideBySideColumn>

<SideBySideColumn>

**In Strapi 5**

A user might still create custom endpoints and handle files with the `ctx` object, but the property names are different:

  ```js
  const endpoint = (ctx) => {
    ctx.request.files.fileName.filepath
    ctx.request.files.fileName.originalFilename
    ctx.request.files.fileName.mimetype
  }
  ```

</SideBySideColumn>

</SideBySideContainer>

## Migration

<MigrationIntro />

### Notes

- The official [`koa-body`](https://github.com/koajs/koa-body/blob/master/CHANGELOG.md) documentation lists the changes.
- The official [`formidable`](https://github.com/node-formidable/formidable/blob/master/CHANGELOG.md#200) documentation lists the changes.

### Manual procedure

Users need to manually update the properties used in their custom code, referring to the official [`koa-body`](https://github.com/koajs/koa-body) and [`formidable`](https://github.com/node-formidable/formidable) documentations.
