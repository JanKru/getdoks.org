---
title: "Diagrams"
description: ""
summary: ""
date: 2023-12-12T08:31:50+01:00
lastmod: 2023-12-12T08:31:50+01:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "diagrams-415fbe1eacef33dede4157f6a606c790"
weight: 420
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Use a fenced code block to embed an SVG image of a diagram in your Doks site using the free [Kroki](https://kroki.io/) service.

{{< callout context="note" icon="info-circle" >}}
Unlike JavaScript solutions that require client-side rendering, this approach embeds an SVG image in your page.
{{< /callout >}}

{{< callout context="tip" icon="rocket" >}}
Hugo supports [GoAT diagrams](https://gohugo.io/content-management/diagrams/#goat-diagrams-ascii) (ASCII diagrams) natively.
{{< /callout >}}

## Overview

Kroki generates diagrams from textual descriptions, and provides a unified API with support for [D2](https://d2lang.com/), [Mermaid](https://mermaid.js.org/intro/), [PlantUML](https://plantuml.com/), and [other diagram types](https://kroki.io/#support).

You can create:

- [Block diagrams](https://kroki.io/examples.html#blockdiag)
- [Container diagrams](https://kroki.io/examples.html#structurizr-container)
- [Gantt diagrams](https://kroki.io/examples.html#gantt)
- [Mind maps](https://kroki.io/examples.html#mind-map)
- [Sequence diagrams](https://kroki.io/examples.html#mermaid-seqdiag)
- [UML diagrams](https://kroki.io/examples.html#uml-diag)
- [Word clouds](https://kroki.io/examples.html#word-cloud)
- [And more…](https://kroki.io/examples.html)

Visit the [Kroki site](https://kroki.io/examples.html) for more examples.

## Examples

### D2

```kroki {type=d2}
# Actors
hans: Hans Niemann

defendants: {
  mc: Magnus Carlsen
  playmagnus: Play Magnus Group
  chesscom: Chess.com
  naka: Hikaru Nakamura

  mc -> playmagnus: Owns majority
  playmagnus <-> chesscom: Merger talks
  chesscom -> naka: Sponsoring
}

# Accusations
hans -> defendants: 'sueing for $100M'

# Offense
defendants.naka -> hans: Accused of cheating on his stream
defendants.mc -> hans: Lost then withdrew with accusations
defendants.chesscom -> hans: 72 page report of cheating
```

````md
```kroki {type=d2}
# Actors
hans: Hans Niemann

defendants: {
  mc: Magnus Carlsen
  playmagnus: Play Magnus Group
  chesscom: Chess.com
  naka: Hikaru Nakamura

  mc -> playmagnus: Owns majority
  playmagnus <-> chesscom: Merger talks
  chesscom -> naka: Sponsoring
}

# Accusations
hans -> defendants: 'sueing for $100M'

# Offense
defendants.naka -> hans: Accused of cheating on his stream
defendants.mc -> hans: Lost then withdrew with accusations
defendants.chesscom -> hans: 72 page report of cheating
```
````

### Mermaid

```kroki {type=mermaid}
sequenceDiagram
  participant Alice
  participant Bob
  Alice->John: Hello John, how are you?
  loop Healthcheck
    John->John: Fight against hypochondria
  end
  Note right of John: Rational thoughts prevail...
  John-->Alice: Great!
  John->Bob: How about you?
  Bob-->John: Jolly good!
```

````md
```kroki {type=mermaid}
sequenceDiagram
  participant Alice
  participant Bob
  Alice->John: Hello John, how are you?
  loop Healthcheck
    John->John: Fight against hypochondria
  end
  Note right of John: Rational thoughts prevail...
  John-->Alice: Great!
  John->Bob: How about you?
  Bob-->John: Jolly good!
```
````

### PlantUML

```kroki {type=plantuml}
@startmindmap
skinparam monochrome true
+ OS
++ Ubuntu
+++ Linux Mint
+++ Kubuntu
+++ Lubuntu
+++ KDE Neon
++ LMDE
++ SolydXK
++ SteamOS
++ Raspbian
-- Windows 95
-- Windows 98
-- Windows NT
--- Windows 8
--- Windows 10
@endmindmap
```

````md
```kroki {type=plantuml}
@startmindmap
skinparam monochrome true
+ OS
++ Ubuntu
+++ Linux Mint
+++ Kubuntu
+++ Lubuntu
+++ KDE Neon
++ LMDE
++ SolydXK
++ SteamOS
++ Raspbian
-- Windows 95
-- Windows 98
-- Windows NT
--- Windows 8
--- Windows 10
@endmindmap
```
````

## Performance

The render hook calls Hugo's `resources.GetRemote` function to request the SVG image from the Kroki API. Hugo caches the result, and invalidates the cache when (a) you edit the LaTeX markup, or (b) the cache expires.

To optimize performance in a CI/CD environment such as [Cloudflare Pages](https://pages.cloudflare.com/), [GitHub Pages](https://pages.github.com/), or [Netlify](https://www.netlify.com/), you should:

1. Edit your site configuration to store the `getresource` cache in the project's `resources` directory, setting the cache to never expire:

    ```toml {title=hugo.toml}
    [getresource]
    dir = ':resourceDir/_gen'
    maxAge = -1
    ```

2. Check the `resources` directory into source control.

In this configuration, Hugo will use the cached resources when building your site locally and remotely, invalidating the cache when you change the LaTeX markup.
