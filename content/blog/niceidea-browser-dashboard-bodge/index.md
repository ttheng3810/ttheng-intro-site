---
title: "Bodging a browser dashboard displaying NiceChord's NiceIdea tips"
date: 2022-12-23
slug: "niceidea-browser-dashboard-bodge"
description: "I bodged existing browser dashboard and NiceIdea codes together to make the dashboard show musical tips in NiceIdea."
keywords: ["niceidea","bodge"]
draft: true
tags: ["music","code"]
math: false
toc: true
---

> *The meaning of the word 'bodge' here is not in [its colloquial sense](https://dictionary.cambridge.org/dictionary/english/botch), but rather what as described in Tom Scott's [*The Art of the Bodge*](https://www.youtube.com/watch?v=lIFE7h3m40U).*

## Background

So, [Wiwi Kuan's NiceChord](https://nicechord.com/about) released a random musical idea generator, aptly named NiceIdea, in 2021. This generator is mainly written in JavaScript, and its source code can be found [here](https://github.com/wiwikuan/NiceIdea).

This generator comes in two versions: an [online version](https://nicechord.com/NiceIdea), and a CLI version for those who are into it. Personally, I really like this generator as it does help me a lot what is usually called 'composer's block'. Among the features provided in the generator, I particularly like the one that randomly generates a handy tip related to music in general.

However, being as lazy as I am, I sometimes find <cite>having to type the URL first[^1]</cite> every time I want to use the idea generator quite troublesome. So, I started to think if there's a way to implement a local version of it where the tips could be shown as I do routine stuff on my laptop, like logging into my desktop or opening a browser.

Initially, I planned to bodge up a desktop widget that seeks to achieve this, but then I realised it might be too difficult of a bodge to me, so I decided to make a browser dashboard (a.k.a. a New Tab page) version of it instead, something like [Momentum Dash](https://momentumdash.com/).

My plan is that I want the browser dashboard to behave such that it shows a random musical tip every time I open my browser.

## Process

These are my rough steps in doing the bodge.

First, I took the code from NiceIdea as well as [Tabliss](https://github.com/joelshepherd/tabliss), a free and open source browser dashboard (which is also great to use and has [multiple useful features](https://web.tabliss.io/)). Tabliss is mostly written in TypeScript whereas NiceIdea is mainly written in JavaScript, so I reckoned it might not be too much of a hassle to incorporate them together.

Luckily, Tabliss has already had a pretty well-built quotes display feature. So, it seems like all I need to do is to just add a new list of quotes with the NiceIdea tips into the Tabliss codebase.


[^1]: If you think that I should've done an online search or even just bookmarked the site ... well, you've got a point, but I still wonder if there's a way such that the tips coudld be shown to me right on my laptop screen.

## Outcome

After several hours, I've completed the work. This is how it turned out.
