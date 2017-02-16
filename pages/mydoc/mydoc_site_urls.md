---
title: Link URLs
keywords: link, url
last_updated: February 15, 2017
tags: [getting_started]
summary: "Configuration of link URLs"
sidebar: mydoc_sidebar
permalink: /mydoc/mydoc_site_urls.html
---

## Site base URL

Jekyll baseurl is explained in [this blog post](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/).

The site `baseurl` can be set in `_config.yml`:

```yaml
baseurl: /test_baseurl
```

{% include important.html content="If the site is at the root of the webserver, baseurl must be empty (the property can even be removed). **Otherwise, do not forget the leading '/' character**." %}

With this configuration, serving the site with `jekyll serve`, the current page will be located at `http://localhost:4000/test_baseurl/mydoc/site_urls.html`, with theses variables:

* `site.url`: `http://mysite`
* `site.baseurl`: `/baseurl`
* `page.path` or `page.url`: `/mydoc/site_urls.html`

## Page URL

Page URL is defined in the `permalink` part of the frontmatter. See [Pages][{{ site.baseurl }}/mydoc_pages] and [Hyperlinks][{{ site.baseurl }}/mydoc_hyperlinks].

In this development branch, page URLs can contain inner sublevels. The current page located at `/mydoc/mydoc_site_urls.html` is provided as example.

{% include important.html content="All page permalinks must begin with a leading '/' character, in order to get links working from a page located in a subfolder." %}

## Links

If the page is referenced in the sidebar, the short link syntax works, as described in [Hyperlinks][{{ site.baseurl }}/mydoc_hyperlinks].

```
[Site URLs][{% raw %}{{ site.baseurl }}{% endraw %}/mydoc/mydoc_site_urls]
```

Here's the result: [Site URLs][{{ site.baseurl }}/mydoc/mydoc_site_urls]

{% include warning.html content="If the link is broken, this link syntax will fails silently." %}

This syntax is equivalent, but if the link is broken, Jekyll will not render the link. So, it is more robust.

```
[Site URLs]({% raw %}{{ site.baseurl }}{% link pages/mydoc/mydoc_site_urls.md %}{% endraw %})
```

Here's the result: [Site URLs]({{ site.baseurl }}{% link pages/mydoc/mydoc_site_urls.md %})

{% include note.html content="The link syntax references the file rather that the permalink. It will still work if the permalink changes but Jekyll will fail at generation time if the file moves or is deleted." %}

{% include links.html %}
