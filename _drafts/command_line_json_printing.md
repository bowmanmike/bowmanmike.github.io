---
title: JSON: Fun for Everyone!
date: 2017-07-06
layout: post
---

## Outline
1. Install `jq`
2. Learn to use it
3. Command line functions
4. Complicated scripts to pull out specific data
  - `cat data/json/listings/onregional-frh-out-of-area.json | jq '[.[]."sale-date" | strptime("%m/%d/%Y") | todate] | sort | last'`
  - Read a json file with +50k entries, pull out the most recent 'sale-date' file
5. Vim functions to prettify/minify json files

Friends! Settle in, I've got a good one for you today. I want to talk to you all about my favourite data-interchange format! What's that? Nobody has a favourite data-interchange format? Nonsense! Everyone has one. Mine is JSON. Heard of it? Yeah, I thought so. It's everywhere in the web world. I'm not going to go into the details of what JSON is in this post, or what it stands for, or where it comes from, but if you're interested in that information, check out [www.json.org](http://www.json.org). What I want to talk about here is some tricks to handling large amounts of JSON in a sane, speedy fashion. Because nobody likes crashing their text editor trying to open a 400mb JSON file holding 85,000 records with upwards of 20 fields each, because they're trying to find out the lowest value of one particular field. Yeah, definitely did that to myself at least once. It took an embarrassingly long time until I realized that there must be a better way, but once I found it, hoooo boy. Things improved, let me tell ya.

So. Down to brass tacks. The first thing I'm gonna need to you to do, is go ahead and download a fun little command-line program called `jq`. You can read about it at [https://stedolan.github.io/jq/](https://stedolan.github.io/jq/). If you're using a Mac, you can install it with Homebrew. Otherwise, there's all kinds of fun instructions if you follow that link. `jq`, if you haven't heard of it, is a command-line JSON parser. It's written in C, and it's super powerful, in the right hands. In the wrong hands, well, luckily for us, it won't do much. At it's most basic, it'll take a single-line JSON string and pretty-print it for you.

This:
```json
{"name": "Mike", "age": 27, "occupation": "developer", "likesPizza": true}
```
Turns into this:
```json
{
  "name": "Mike",
  "age": 27,
  "occupation": "developer",
  "likesPizza": true
}
```

Not a huge deal when you're dealing with such a short string, but it gets useful once the dataset gets any bigger
