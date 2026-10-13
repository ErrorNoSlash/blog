+++
title = 'How I built this blog'
slug = 'How I built this blog'
date = '2026-07-24'
taxonomies.tags = [
	'zola',
	'nixos',
	'meta',
]
+++
Every blog needs a first post, and the least original — but most honest — thing I can write about is the blog itself. So: here's what's holding this page up, and the one thing that fought me the whole way.

## The stack

It's a [Zola]([https://www.getzola.org/](https://www.getzola.org/)) site. I choose Zola because its written in rust and is open source wanted something fast and open. It also gives me much more freedom then other blogging tools would give.

On top of it sits the [Terminus]([https://github.com/klritunu/terminus](https://github.com/klritunu/terminus)) theme, which gives me the `dias@stas:~/blog $` terminal look for basically free. I swapped in my own custom palette and a custom stylesheet so i could customize and make it mine.

Deploy is a GitHub Actions workflow: push to `main`, it builds the site and publishes it to `blog.errornoslash.be`. No server to babysit — the output is just files.

## Editing without touching the terminal

The part I actually wanted was to write posts *without* opening an editor and hand-writing TOML front-matter every time. That's where [Pages CMS]([https://pagescms.org/](https://pagescms.org/)) comes in. It reads a `.pages.yml` schema straight out of the repo, then gives me a proper form — title, slug, date, tags, a rich-text body — and commits the resulting Markdown back to GitHub for me. The post you're reading was written through that form.

The nice bit is that the CMS is *just a view* onto the repo. If it ever disappears, my posts are still plain `.md` files sitting in `content/blog/`. No lock-in, no export dance.

## What broke

The hardest part was setting up the custom stylesheet. It broke a lot as Zola expects a very specific format. The colors also sometimes broke but where easy to fix. Setting up Zola and linking it to the repo also failed a few times. But overall it went pretty smooth

## What's next

Now that the pipeline works end to end, the plan is to actually use it: write-ups of the projects I've been building and the NixOS config I keep poking at more than is strictly necessary.

If you're reading this, the deploy worked. See you in the next one.