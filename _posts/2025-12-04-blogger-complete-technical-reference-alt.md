---
layout: post
title: "Blogger Complete Technical Reference"
date: 2025-12-04 12:45:00 -03:00
categories: [Tecnología, Blogger]
---

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTRqMd6J0HNfNdQercqlwHw5eLYJMjw7E-RnFn7UfJuJuvoPA5ckBr9E)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTRqMd6J0HNfNdQercqlwHw5eLYJMjw7E-RnFn7UfJuJuvoPA5ckBr9E)

_A comprehensive reference of Blogger’s public URLs, API endpoints, feeds, parameters, template data-tags, comment anchors, archive structures, and internal dashboard routes._

# Overview

This document compiles every known and verified resource from:

- Blogger public pages
- Blogger internal dashboard routes
- Blogger Atom/RSS feed system
- Google Blogger API v3
- Blogger template engine (`data:` tags)
- Comment system internal anchors
- Undocumented parameters that are confirmed to work

## Placeholder conventions

| Placeholder | Meaning |
| --- | --- |
| `{blogUrl}` | Blog hostname, without protocol |
| `{customDomain}` | Custom domain hostname |
| `{blogId}` | Numeric blog ID |
| `{postId}` | Numeric post ID |
| `{pageId}` | Numeric static page ID |
| `{postSlug}` | Post slug |
| `{pageSlug}` | Static page slug |
| `{year}` | Year |
| `{month}` | Month |
| `{label}` | Label or tag |
| `{query}` | Search query |
| `{commentId}` | Numeric comment ID |
| `{apiKey}` | API key |

## Public URLs

```text
https://{blogUrl}/
https://{blogUrl}/{year}/{month}/{postSlug}.html
https://{blogUrl}/search/label/{label}
https://{blogUrl}/search?q={query}
https://{blogUrl}/{year}/{month}/
```

## Feed endpoints

```text
https://{blogUrl}/feeds/posts/default
https://{blogUrl}/feeds/posts/default?alt=atom
https://{blogUrl}/feeds/comments/default
https://{blogUrl}/feeds/posts/default/-/{label}
```

## API v3

```text
https://www.googleapis.com/blogger/v3/
GET users/{userId}/blogs
GET blogs/{blogId}
GET blogs/{blogId}/posts
GET blogs/{blogId}/posts/{postId}
GET blogs/{blogId}/pages
```

This is a useful reference when you want to inspect how Blogger exposes content and automate around it.
