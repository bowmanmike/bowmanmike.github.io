---
title: Command Line JSON Printing
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
