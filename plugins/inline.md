---
title: Inline
description: Using the inline plugin to inline sources
docs: plugins/inline.ts/~/Options
tags:
  - html
---

${toc}

## Installation

Import this plugin in your `_config.ts` file to use it:

```js
import lume from "lume/mod.ts";
import inline from "lume/plugins/inline.ts";

const site = lume();

site.use(inline({/* your config here */}));

export default site;
```

See
[all available options in Deno Doc](https://doc.deno.land/https/deno.land/x/lume@/plugins/inline.ts/~/Options).

## Description

This plugin allows to inline some sources, like CSS, images or JavaScript, in
the HTML automatically. Any HTML tag with the `inline` attribute will be
included in the HTML. For example:

<lume-code>

```html {title="Input"}
<link rel="stylesheet" href="/css/my-styles.css" inline>

<script src="/js/my-scripts.js" inline></script>

<img src="/img/avatar.png" inline>

<img src="/img/logo.svg" inline>
```

```html {title="Output"}
<style>
  /* Content of /css/my-styles.css */
</style>

<script>
  // Content of /js/my-scripts.js
</script>

<img src="data:image/png;base64,...">

<svg>...</svg>
```

</lume-code>

Note that bitmap images will be inlined as base64 data but svg images are
replaced by the `<svg>` element. {.tip}

The source file must be exported to the `dest` directory, there's no support for
external URLs. {.tip}