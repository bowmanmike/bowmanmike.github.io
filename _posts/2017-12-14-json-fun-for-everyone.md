---
title: "JSON: Fun for Everyone!"
date: 2017-12-14
layout: post
---

Friends! Settle in, I've got a good one for you today. I want to talk to you all about my favourite data-interchange format! What's that? Nobody has a favourite data-interchange format? Nonsense! Everyone has one. Mine is JSON. Heard of it? Yeah, I thought so.

It's everywhere in the web world. I'm not going to go into the details of what JSON is in this post, or what it stands for, or where it comes from, but if you're interested in that information, check out [www.json.org](https://www.json.org). What I want to talk about here is some tricks to handling large amounts of JSON in a sane, speedy fashion. Because nobody likes crashing their text editor trying to open a 400mb JSON file holding 85,000 records with upwards of 20 fields each, because they're trying to find out the lowest value of one particular field. Yeah, definitely did that to myself at least once. It took an embarrassingly long time until I realized that there must be a better way, but once I found it, hoooo boy. Things improved, let me tell ya.

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

Not a huge deal when you're dealing with such a short string, but the real power comes out when you start operating on a bigger dataset.

Take, for example, the aforementioned 400mb, 85,000 record JSON file. Try opening that in any text editor and you'll have a bad time. Even worse, try searching for a particular value within that text editor. It's trouble. Trust me, I've tried. This is where `jq` really shines. Let's say that you want to pull out the most recent timestamp from a record in that file. Print the file with `cat`, pipe the output to `jq`, and provide a complex-looking set of arguments. Ta-Da! You've got the value. The full command looks like this:
```bash
cat ~/path/to/file.json | jq '[.[]."timestamp" | strptime("%m/%d/%Y") | todate] | sort | last'
```
Without going into too much detail, the arguments passed to `jq` allow you to access particular fields on each object, parse them to a standard timestamp format, sort them, and take the last. Operating on the 400mb file, it takes about a second to run that command. Pretty impressive, if you ask me.

Another recent use case I found is to return records that match a particular filter. Say you want to pull all records matching a particular name.
```bash
cat ~/path/to/file.json | jq '.[] | select(.name == "mike")'
```
Pretty neat huh?

#### Other Fun JQ Stuff
As some of you may know, I'm a fan of Vim (well, specifically Neovim) for the vast majority of my code editing needs. Vim integrates super well with command line tooling like `jq`, so I've got a few useful little custom vim functions to manipulate JSON in a sane way. I like to have the ability to minify or prettify my JSON files as I'm workin, and in Vim, invoking `jq` from within the editor is dead easy. I've got two short VimScript functions that I've mapped to easy shortcuts.
```vimscript
function PrettyPrintJSON()
  :%!jq '.' -M
endfunction

function! MinifyJSON()
  :%!jq '.' -cM
endfunction
```
I know I'm not the only person to do this, and I think I found [this](https://pascalprecht.github.io/2014/07/10/pretty-print-json-in-vim/) post, which I used as inspiration for my functions, but feel free to shamelessly copy these and make them your own.

That's all I've got for the moment! Happy data-interchanging!

#### Related Links
- [jq documentation](https://stedolan.github.io/jq)
- [JSON specification](https://json.org)
- [My vim config](https://github.com/bowmanmike/dotfiles/blob/master/.vimrc)
