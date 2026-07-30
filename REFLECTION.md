# Reflection

## What I repeated by hand:

The biggest thing was the `<head>` block. Every single page has the same doctype plus meta tags plus four `<link>` stylesheets, and the only things that actually differ per page are the `<title>` line along with the `<meta name="description">`. Later I decided to swap in Google Fonts for a warmer look using Fraunces paired with Nunito, which meant opening all nine pages one by one to paste the same font `<link>` into each one.

The header along with the nav and the footer were the same story. Nine identical copies of the same markup, with the only real difference being which nav link gets `aria-current="page"` depending on the page.

The family pages were the worst offender though. `fresh.html`, `soft.html`, `blue.html`, plus `hard.html` are basically the same page four times over. They each have a hero image, then the same four content sections, then prev/next links at the bottom. I built the first one, then copy-pasted it three times, swapping out the content along with the image src for each new family.

## What broke (or almost did):

I already knew from class along with the assignment description that relative paths were going to be the trap, so I was careful with them from the start. Root pages reference `styles/tokens.css` directly while guide pages need `../styles/tokens.css`, so I had to keep that straight in my head every time I linked a stylesheet. The two `index.html` files were the other confusing part, since there is one at the site root plus one inside `guide/`, with both getting linked as `href="index.html"` from a page in their own folder. I had to double-check which file I was actually editing whenever I made changes.

## What I want a tool to generate:

The most obvious thing is a layout template with slots for `title` plus `description` plus `main`, so the shared skeleton could live in one file instead of nine. I would also want auto-computed relative paths so I could just write `styles/tokens.css` once, letting the tool figure out when to add `../`. For the family pages specifically, a data-driven approach would be huge: one template plus one data file with four entries would generate all four pages with the correct prev/next links between them, no copy-pasting required.

That said, some of the new browser features genuinely surprised me with how much they can do without JavaScript. Between `:has()` plus invoker commands plus view transitions, I was able to build a fake-submit poll on the guide page, a "Why join?" dialog on the join page, along with a cheese fact popover on the home page, all using plain HTML paired with CSS. The platform is closing a lot of gaps that frameworks used to fill, but templating along with code-generation is still very much where the pain lives.