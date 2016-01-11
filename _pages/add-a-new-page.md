---
title: Add a new page
---
To add new pages, create a 
[Markdown](http://daringfireball.net/projects/markdown/syntax) file in the
`_pages/` directory of the repository. For example, the Markdown text for
this page is
[`_pages/new-page.md`](https://github.com/18F/guides-template/blob/18f-pages/_pages/add-a-new-page.md).

The Markdown document begins with this [YAML front
matter](http://jekyllrb.com/docs/frontmatter/):

```yaml
---
title: {{ page.title }}
---
```

For most pages this will suffice. The URL of the page will match the file path
relative to the `_pages` directory, minus the `.md` extension. For example,
the source for this page appears as
[`{{ page.path }}`]({{ site.repos[0].url }}/tree/18f-pages/{{ page.path }}).

For the home page of your guide, the front matter should contain a
`permalink: /` entry like this:

```yaml
---
permalink: /
title: Introduction (or whatever title you choose)
---
```

You can also explicitly set a `permalink:` like so:

```yaml
---
permalink: {{ page.url }}
title: {{ page.title }}
---
```

If you add your own custom `permalink:`, **the '`/`' at the end of the
`permalink:` attribute is important!** It ensures the page is generated as
`{{ page.url }}index.html`. Without it, the page generates as
`/{{ page.url | remove_first: '/' | replace:'/','.'}}html`.

## Link to other pages within the guide

Every link to another page _must_ be prefixed with
`{% raw %}{{ site.baseurl }}{% endraw %}`. For example,
this link to [Add images]({{ site.baseurl }}/add-images/)
appears in the Markdown source as:

```
{% raw %}[Add images]({{ site.baseurl }}/add-images/){% endraw %}.
```

## Next steps

Click the _Add images_ entry in the table of contents to learn how
to add images to your guide, or click _Make a child page_ to see how to
make chapters appear as children of related chapters.