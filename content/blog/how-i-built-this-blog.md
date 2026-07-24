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
+++

title = "How I built this blog"

date = 2026-07-24

  


[taxonomies]

tags = ["zola", "nixos", "meta"]

+++

  


Every blog needs a first post, and the least original — but most honest —

thing I can write about is the blog itself. So: here's what's holding this

page up, and the one thing that fought me the whole way.

  


**## The stack**

  


It's a [Zola](++[https://www.getzola.org/](https://www.getzola.org/)++) site. One static-site-generator

binary, no Node, no 400-package `node_modules` to audit. I write Markdown,

Zola spits out HTML, and that's the whole content pipeline.

  


On top of it sits the [Terminus](++[https://github.com/klritunu/terminus](https://github.com/klritunu/terminus)++)

theme, which gives me the `dias@stas:~/blog $` terminal look for basically

free. I swapped in my own `errorno-dark` palette and a custom stylesheet so

it feels like mine and not a demo, but the bones are all Terminus.

  


Deploy is a GitHub Actions workflow: push to `main`, it builds the site and

publishes it to `blog.errornoslash.be`. No server to babysit — the output is

just files.

  


**## Editing without touching the terminal**

  


The part I actually wanted was to write posts *without* opening an editor and

hand-writing TOML front-matter every time. That's where

[Pages CMS](++[https://pagescms.org/](https://pagescms.org/)++) comes in. It reads a `.pages.yml` schema

straight out of the repo, then gives me a proper form — title, slug, date,

tags, a rich-text body — and commits the resulting Markdown back to GitHub for

me. The post you're reading was written through that form.

  


The nice bit is that the CMS is *just a view* onto the repo. If it ever

disappears, my posts are still plain `.md` files sitting in `content/blog/`.

No lock-in, no export dance.

  


**## What broke**

  


Naturally, the friction wasn't the CMS or Zola — it was *logging in*.

  


Getting into Pages CMS means authenticating with GitHub, and I use a passkey

stored in Proton Pass. On a Firefox-based browser (I'm on Zen), that handoff

isn't automatic: Firefox routes the WebAuthn request straight to the OS

platform authenticator, so instead of a nice Proton Pass popup I got the

system's *"Touch your security key"* dialog and GitHub grumbling about

"partial passkey support." The extension never got a look in.

  


The fix lives in `about:config`, and the annoying part on a declarative NixOS

setup is making sure the pref survives a rebuild instead of getting reset the

next time I `switch`. Lesson filed under *"the login page is always harder

than the app."*

  


**## What's next**

  


Now that the pipeline works end to end, the plan is to actually use it:

write-ups of the projects I've been building and the NixOS config I keep

poking at more than is strictly necessary.

  


If you're reading this, the deploy worked. See you in the next one.