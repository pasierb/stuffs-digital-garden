---
layout: editorial
---

# Free blog setup with GitHub and Hugo

I recently moved my blog from Wordpress hosted on DigitalOcean to [Hugo](https://gohugo.io/) hosted on [GitHub pages](https://pages.github.com/). Here's how and why I did it.

## Why?

Because I'm cheap and spending \~10$/month for a blog that gets close to 0 traffic and close to 0 attention from the owner hurts my onion hearth.

## What's Hugo?

[Hugo](https://gohugo.io/) is a static site generator (SSG) written in Go. It's main strength is speed of generation, but I like it for other reasons:

* Convention over configuration
* "All you need" features out of the box
* Maybe not the biggest but definitely high quality community
* Easy to understand, no magic source code
* Markdown 💖

## Migrating content

Hugo content is written in Markdown so I had to transform it. And since my blog had at the time enormous amount of content, i.e. 2 posts, I did that manually using .

The easiest way is to simply open each blog post, inspect the source in Chrome, find the first wrapping dom node in the inspector, right click and select "Copy outerHTML". Paste result in to https://codebeautify.org/html-to-markdown and enjoy freshly baked Markdown.

_If You need your old posts to appear under the same URL You can use_ [_`aliases`_](https://gohugo.io/content-management/front-matter/#predefined) _field in post frontmatter._

## Hosting

GitHub distingushes 3 types of pages: personal, organization and project. Since it's a personal blog I followed the guidelines for that type. In this case GitHub requires that the repo must be named after the username, in my case `https://github.com/pasierb/pasierb`. Side benefit of this naming scheme is that the repo's README becomes your [profile README](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme).

I was worried that I will need to learn GitHub Actions to run hugo build, but suprisingly once GitHub notices that the repo is a Hugo project I got predefined build configuration suggested and it works flowlessly (awesome job GH!).

## Custom domain

To set up custom domain for GitHub Pages I had to verify that I own the domain, which boils down to setting some TXT record in DNS.

On thing that I noticed once the project was available at `www.stuffs.dev` is that assets are not loading and paths are wrong. Turns out that Hugo be default uses relative paths which is problematic since GH Pages uses username path prefix, e.g. `pasierb.github.io/PASIERB`. In order for things to work correctly with path prefix I had to force Hugo to use absolute paths when generating HTMLs. Fortunately it's as easy as setting `canonifyURLs = true` in `config.toml`. That's it!

## Conclusion

Moving everything took me probably less than 2h which I find a great result. Developer experience both on GitHub side as well as Hugo is top notch. 10$/month more in my pocket is also top notch 🤑.
