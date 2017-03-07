---
layout: post
date: 2017-03-06
title: Cleaning Up Conditionals with Send
---

Well well well, here we are. In the words of a song my friend wrote for our band in high school, "It's been so long, but now we're back." Lyrical genius, I say. Anyways, it's been quite a while since I posted, but I thought I might try and resurrect this blog a little with some slightly more technical content. I've been programming pretty much every day for over a year now, and I feel like I've done some kinda cool things. Lets dive in!

So I wanna talk a bit about something cool I learned at work a few months back. I'd been working with large, somewhat irregular JSON files, and had to parse certain values out of the data. The fields would come in different forms, sometimes a string, sometimes an array, sometimes a hash. My first attempt at solving the issue looked something like this:  
```ruby
if input.is_a?(String)
  call_string_method(input)
elsif input.is_a?(Array)
  call_array_method(input)
elsif input.is_a?(Hash)
  call_hash_method(input)
end
```

It gets the job done, and to my novice programming brain, it was the proper way to do it. But what happens when you decide in the future that you need to handle a `Float` differently from an `Integer`? Or that you want to add custom objects to the tree? You can add as many `elsif` lines to an if statement as you want, but it's ugly and hard to reason about. My boss showed me this cool way of handling this kind of issue, which has been a standard in my toolbox ever since that day.

First, we define the handler methods we'd need anyways.  
```ruby
def handle_string(input)
  # do stuff
end

def handle_array(input)
  # do stuff
end

def handle_hash(input)
  # do stuff
end
```

Then, we find the class of the `input`, and using a clever combination of the `Object#send` method and string interpolation, we call the method dynamically, like this.  
```ruby
input_klass = input.class.to_s.downcase
send("handle_#{input_klass}", input)
```
Isn't that much cleaner? We get the string value of the class of `input`, and call the `send` method with a string with some interpolation as the first argument, and our `input` object as the second argument.

`send` is a cool little method, defined on the `Object` class, which is the parent of just about every Ruby class. Basically, it identified a method by it's name as a string, and calls it with whatever arguments are passed along. This allows you to call methods using string interpolation to call one or the other, rather than using a complicated set of `if-else` blocks to make that decision. The documentation is [here](http://ruby-doc.org/core-2.4.0/Object.html#method-i-send) if you want to read more.

That's about all I got for now, but thanks for reading, and I hope someone out there finds this useful!
