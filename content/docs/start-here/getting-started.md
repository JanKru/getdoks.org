---
title: "Getting Started"
description: ""
summary: ""
date: 2023-09-12T12:07:48+02:00
lastmod: 2023-09-12T12:07:48+02:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "getting-started-cefa9dc0267d0e3bb7a88365c6178eb1"
weight: 110
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Doks is a full-featured documentation theme built on top of the [Hyas](https://gethyas.com/) framework. This guide will help you get started with a new project. See the [manual setup instructions](/docs/start-here/manual-setup/) to add Doks to an existing Hyas project.

## Quick Start

### Create a new project

Create a new Hyas + Doks project by running the following command in your terminal:

{{< tabs "create-new-site" >}}
{{< tab "npm" >}}

```bash
npm create hyas@latest -- --template doks
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm create hyas@latest -- --template doks
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn create hyas@latest -- --template doks
```

{{< /tab >}}
{{< /tabs >}}

This will create a new [project directory](/docs/basics/project-structure/) with all the necessary files and configurations for your site.

{{< callout context="tip" title="See it in action" icon="rocket" >}}
Try Doks in your browser: [open the template on Gitpod](https://gitpod.io/#https://github.com/gethyas/doks).
{{< /callout >}}

### Install dependencies

`cd` into your new project directory and install your dependencies before continuing.

{{< tabs "install dependencies" >}}
{{< tab "npm" >}}

```bash
npm install
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm install
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn install
```

{{< /tab >}}
{{< /tabs >}}

### Start the development server

When working locally, Hugo's development server lets you preview your work and automatically refreshes your browser when you make changes.

Inside your project directory, run the following command to start the development server:

{{< tabs "start-development-server" >}}
{{< tab "npm" >}}

```bash
npm run dev
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm dev
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn dev
```

{{< /tab >}}
{{< /tabs >}}

This will log a message to your terminal with the URL of your local preview. Open this URL to start browsing your site.

### Add content

Doks is ready for you to add new content, or bring your existing files!

#### File formats

Doks supports authoring content in Markdown and HTML with no configuration required. You can add support for Emacs Org-Mode, AsciiDoc, RST, and Pandoc by installing [additional parsers](https://gohugo.io/content-management/formats/#list-of-content-formats).

#### Add pages

Add new pages to your site by creating `.md` or `.html` files in `content/docs/`. Use sub-folders to organize your files and to create multiple path segments.

For example, the following command will generate a page at `example.com/docs/guides/faq`:

{{< tabs "create-new-page" >}}
{{< tab "npm" >}}

```bash
npm run create docs/guides/faq.md
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm run create docs/guides/faq.md
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn run create docs/guides/faq.md
```

{{< /tab >}}
{{< /tabs >}}

#### Frontmatter

All Doks pages share a customizable [common set of frontmatter properties](/docs/reference/frontmatter/) to control how the page appears — for documentation pages:

```md
---
title: "Example Guide"
description: ""
summary: ""
date: 2023-09-07T16:04:48+02:00
lastmod: 2023-09-07T16:04:48+02:00
draft: true
menu:
  docs:
    parent: ""
    identifier: "example-6a1a6be4373e933280d78ea53de6158e"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
```

### Next steps

- **Configure**: Learn about common options in ["Customizing Doks"](/docs/guides/customization/).
- **Menus**: Set up your menus with the ["Menus"](/docs/basics/menus/) guide.
- **Shortcodes**: Discover built-in callouts, tabs, and more in the ["Shortcodes"](/docs/basics/shortcodes/) guide.
- **Deploy**: Publish your work with the ["Deploy your site"](https://docs.gethyas.com/guides/deploy/) guide in the Hyas docs.

## Updating Doks

Doks is a Hyas theme, and is updated like any `@hyas/*` theme (or integration):

{{< tabs "update-doks" >}}
{{< tab "npm" >}}

```bash
npm install @hyas/doks-core@latest
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm upgrade @hyas/doks-core --latest
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn upgrade @hyas/doks-core --latest
```

{{< /tab >}}
{{< /tabs >}}

See the [Doks changelog](https://github.com/gethyas/doks-core/blob/main/CHANGELOG.md) for a full list of the changes made in each release.

## Troubleshooting Doks

Use the [project configuration](/docs/reference/configuration/) and [individual page frontmatter configuration](/docs/reference/frontmatter/) reference pages to ensure that your Doks site is configured and functioning properly. See the guides in the sidebar for help adding content and customizing your Doks site.

If your answer cannot be found in these docs, please visit the [full Hyas Docs](https://docs.gethyas.com/) for complete Hyas documentation. Your question may be answered by understanding how Hyas works in general, underneath this Doks theme.

You can also check for any known [Doks issues on GitHub](https://github.com/gethyas/doks/issues), and get help in [Doks Discussions](https://github.com/gethyas/doks/discussions) from our active, friendly community!
