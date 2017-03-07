---
layout: post
date: 2017-03-06
title: Basic Metaprogramming in Ruby
---

So the term "metaprogramming" sounds big and scary. And it kinda is. If you look it up on [Wikipedia](https://en.wikipedia.org/wiki/Metaprogramming), you get a long scary article about some kinda logic and stuff. I'm sure there's useful material buried somewhere in there, but I haven't had the time to go digging just yet. For the purposes of this post, let's think of metaprogramming as a program *changing itself* at runtime. Sound spooky? Matrix-y? HAL-9000-ish? It's not. I promise.

I first was exposed to this in the wild a few weeks ago at work. I was coding away, happy as a clam in front of a computer, when I came across a pretty standard problem. The project I was working on could accept various types of data as input, and it needed to run similar, but different, methods depending on the data type. I'd already rigged up the `send` method to call methods dynamically, rather than building giant, incomprehensible chains of conditionals. If you haven't used `send` in Ruby before, check out [this other post I wrote]({% post_url 2017-03-06-cleaning-up-conditionals-with-send %}).

Talk about metaprogramming.

`define_singleton_method`
