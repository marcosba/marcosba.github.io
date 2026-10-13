---
layout: post
title: "Blogger Complete Technical Reference"
date: 2025-12-04 12:45:00 -03:00
categories: [Tecnología, Blogspot]
---

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTRqMd6J0HNfNdQercqlwHw5eLYJMjw7E-RnFn7UfJuJuvoPA5ckBr9E)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTRqMd6J0HNfNdQercqlwHw5eLYJMjw7E-RnFn7UfJuJuvoPA5ckBr9E)

_A comprehensive reference of Blogger’s public URLs, API endpoints, feeds, parameters, template data-tags, comment anchors, archive structures, and internal dashboard routes._

# 1. Overview

This document compiles every known and verified resource from:

- Blogger public pages
- Blogger internal dashboard routes
- Blogger Atom/RSS feed system
- Google Blogger API v3
- Blogger template engine (`data:` tags)
- Comment system internal anchors
- Undocumented parameters that are confirmed to work

All placeholders follow real-world conventions used by Blogger.

---

# 2. Placeholder Conventions

| Placeholder | Meaning |
| --- | --- |
| `{blogUrl}` | Blog hostname, without protocol, e.g. `example.blogspot.com` |
| `{customDomain}` | Custom domain hostname, e.g. `example.com` |
| `{blogId}` | Numeric blog ID used by the API |
| `{postId}` | Numeric post ID |
| `{pageId}` | Numeric static page ID |
| `{postSlug}` | Post slug appearing in URL |
| `{pageSlug}` | Static page slug |
| `{year}` | Four-digit year (`2024`) |
| `{month}` | Two-digit month (`01`) |
| `{label}` | Label / tag |
| `{query}` | Search query |
| `{commentId}` | Numeric comment ID |
| `{commentAnchor}` | Internal anchor for specific comment (`c1234567890`) |
| `{userId}` | Google/Blogger user ID |
| `{profileId}` | ID used for public profile pages |
| `{apiKey}` | Blogger API key |

---

# 3. Public URLs

These URLs work for Blogger and custom domains unless otherwise stated.

## 3.1 Blog Home

```text
https://{blogUrl}/
https://{blogUrl}/?m=1
?view=classic
?view=flipcard
?view=mosaic
?view=sidebar
?view=snapshot
?view=timeslide
```

## 3.2 Posts

```text
https://{blogUrl}/{year}/{month}/{postSlug}.html
https://{blogUrl}/{year}/{month}/{postSlug}.html?m=1
https://{blogUrl}/{year}/{month}/{postSlug}.html?showComment={commentId}#c{commentId}
https://{blogUrl}/{year}/{month}/{postSlug}.html?maxResults={number}
https://{blogUrl}/{year}/{month}/{postSlug}.html?sortBy=newest
```

## 3.3 Static Pages

```text
https://{blogUrl}/p/{pageSlug}.html
```

## 3.4 Labels

```text
https://{blogUrl}/search/label/{label}
https://{blogUrl}/search/label/{label}?m=1
https://{blogUrl}/search/label/{label}?max-results={number}
```

## 3.5 Search

```text
https://{blogUrl}/search?q={query}
```

## 3.6 Archives

```text
https://{blogUrl}/{year}/{month}/
https://{blogUrl}/{year}_{month}_01_archive.html
```

## 3.7 Comments

```text
https://{blogUrl}/{year}/{month}/{postSlug}.html#comment-form
```

## 3.8 Profile Pages

```text
https://www.blogger.com/profile/{profileId}
```

---

# 4. URL Parameters

- `?m=1` → mobile view
- `?view=` → force a theme layout
- `?showComment=` → scroll to a comment
- `#c{commentId}` → comment anchor
- `?maxResults=` → limit posts or comments
- `?sortBy=` → sort ordering
- `?by-date=` → sort search or label results
- `?updated-min=` / `?updated-max=` → filter by date

---

# 5. Feed Endpoints

```text
https://{blogUrl}/feeds/posts/default
https://{blogUrl}/feeds/posts/default?alt=atom
https://{blogUrl}/feeds/comments/default
https://{blogUrl}/feeds/comments/default?alt=atom
https://{blogUrl}/feeds/posts/default/-/{label}
https://{blogUrl}/feeds/{postId}/comments/default
```

---

# 6. Blogger API v3

Base endpoint:

```text
https://www.googleapis.com/blogger/v3/
```

Common endpoints:

```text
GET users/{userId}/blogs
GET blogs/{blogId}
GET blogs/byurl?url=https://{blogUrl}
GET blogs/{blogId}/posts
GET blogs/{blogId}/posts/{postId}
GET blogs/{blogId}/posts/search?q={query}
GET blogs/{blogId}/posts/{postId}/comments
GET blogs/{blogId}/pages
GET users/{userId}
```

---

# 7. Internal Dashboard URLs

These are authenticated dashboard routes used internally by Blogger:

```text
https://draft.blogger.com/blog/posts/{BLOG_ID}
https://draft.blogger.com/blog/comments/{BLOG_ID}
https://draft.blogger.com/blog/settings/{BLOG_ID}
```

---

# 8. Comment Anchors

Blogger uses comment anchors like:

```text
#c{commentId}
```

And sometimes they are combined with:

```text
?showComment={commentId}#c{commentId}
```

---

# 9. Template Data Tags

Blogger exposes structured metadata through `data:` tags, including:

- `data:blog.title`
- `data:blog.url`
- `data:blog.pageType`
- `data:post.title`
- `data:post.url`
- `data:post.id`
- `data:post.body`
- `data:post.labels`
- `data:post.author`
- `data:comment.id`
- `data:comment.author`

---

# 10. Domain Behavior

- Blogspot domains: `https://{blogName}.blogspot.com/`
- Custom domains: `https://{customDomain}/`
- Blogger redirects and canonical behavior are applied automatically
- HTTPS is enforced automatically

---

# 11. Notes & Limitations

- Some undocumented parameters may change without notice.
- API v3 is the supported version.
- Feed endpoints are legacy but still useful.
- Slugs cannot be fully controlled.
- Comment anchors are stable and useful for deep linking.

Este artículo es especialmente útil si querés mapear rutas de Blogger, depurar feeds o construir cosas sobre la plataforma sin adivinar.
