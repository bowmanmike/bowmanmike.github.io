---
layout: post
date: 2016-02-11
title: Syntactic Gymnastics
---

So this week’s been a bit of a change of pace. We’ve shifted gears from Ruby and Rails, and have been learning [Javascript](http://www.javascript.com). Javascript, for those who are unfamiliar, is one of the most widely used programming languages in the world (according to [these guys](https://blog.newrelic.com/2015/07/07/popular-programming-languages/), or [these guys](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)). It’s currently the only language that runs in ever web browser. This means that you–yes, YOU, dear reader, have access to Javascript in all it’s glory. Just try it out for a second here. If you’re using Google Chrome as your browser (which everyone in the world does, right?), hold down the *Command* and *Option* keys, and press “J”. For the Windows folks among us, *CTRL* + *SHIFT* + *J* is the equivalent. Something like this should appear on the side or bottom of your browser.

<span class="image-caption">Javascript console in Chrome Developer Tools</span>
![Chrome console](/assets/chrome-console-screenshot.png)

This is the console. It’s the window into the wonderful world of Javascript. Try stuff! Google “fun things to do in javascript,” and see what happens. Click in the console and type *console.log(“Mike made me do this”)*. Get a little fancier and type *alert(“Isn’t this weird?”)*. Fiddle around, it’s a sandbox, you won’t break anything. It’s just kinda fun to play with. And where I’ve been spending almost all my time for the past week.
So you’ve used the console, you’ve played with Javascript. “But wait,” you ask, “Mike, I thought you were learning Ruby! What’s with the Javascript?” Well, they serve different purposes, though at the core, they can do a lot of the same things. Ruby is great for telling a website what to do. What information to display on the page, what webpage to show you when you visit a particular URL, things like that. Javascript is great at making your webpage “jiggly,” as one of my classmates described it. Any time the content on a webpage changes, it’s probably Javascript. They also look super different. Ruby is meant to be easy for the developer to use. It’s syntax is pretty similar to natural English, at least as far as programming languages go. Javascript looks a lot more like what people tend to expect programming languages to look like. There’s significant syntax to learn, which will break your program if not followed. Here’s a side by side. Try and figure out what each program does before you read any further. Ruby on top, Javascript underneath.

<span class="image-caption">FizzBuzz in Ruby</span>
{% highlight ruby linenos %}
def fizz_buzz
  (1..100).each do |number|
    if (number % 5 == 0 && number % 3 == 0)
      puts "FizzBuzz"
    elsif number % 5 == 0
      puts "Fizz"
    elsif number % 3 == 0
      puts "Buzz"
    else
      puts number
    end
  end
end
{% endhighlight %}

<span class="image-caption">FizzBuzz in Javascript</span>
{% highlight javascript linenos %}
function fizzBuzz() {
  for(i = 0; i < 101; i++) {
    if (i % 5 === 0 && i % 3 === 0) {
      console.log("FizzBuzz");
    } else if (i % 5 === 0) {
      console.log("Fizz");
    } else if (i % 3 === 0) {
      console.log("Buzz");
    } else {
      console.log(i);
    }
  }
}
{% endhighlight %}

This is a common, entry-level programming challenge called FizzBuzz. The objective is to write a short program that will print out all the numbers between one and a hundred. The trick is that if a number is a multiple of 5, print “Fizz” instead, if it’s a multiple of 3, print “Buzz,” and if it’s a multiple of both 3 and 5, print “FizzBuzz. It’s a short program, but it’s interesting to illustrate the differences between languages. (If you’re interested in the differences between languages, check out [this website](http://rosettacode.org/wiki/Rosetta_Code), which provides solutions to various problems written in bazillions of different programming languages. It’s pretty cool stuff.)

(You can type the Javascript example into the Chrome console, and then after that, type “fizzBuzz()”, and it should run the function. Give it a shot.)

(The Ruby one you actually should also be able to run, as long as you’re on a Mac. Open Terminal, type “irb.” This loads the Ruby version of the Javascript console. It’s a Ruby sandbox, you can’t break anything here. Type the Ruby example line-by-line, carefully. Once you’re done, you should be able to type “fizz_buzz” to call the method and see the numbers printed out. Once you’re done, just type “quit” to leave irb, and quit the terminal app.)

You might look at the two and think “How could anyone use Javascript? It looks like robotalk.” And you’d be kinda right. It does. But I’ve actually found that I like writing Javascript. Something about the syntax requirements (which are much stricter), all the brackets, semi-colons, and for-loops (that weird-looking contraption at the top that encapsulates the entire rest of the function), I find oddly satisfying. And, the text editors used to write code have tons of features to make our lives easier, like automatically adding the closing bracket whenever you type the first. I use a program called [Atom](http://atom.io), which is free and (surprise surprise), open-source. It also automatically adds the syntax highlighting, which is fun. It makes me feel like I’m in a movie or something.

Anyways. It’s Javascript week, and it’s going really well. Yesterday we started learning about jQuery, which is basically a giant Javascript file someone (or several someones) wrote, which allows the average developer to get more done, with less. It lets you use Javascript to modify elements on the page, move things around, add things, delete things, make things pop up, and so on. [jQuery](http://www.jquery.com) is used on something like 65% of the top 10,000 most popular websites. You’ve definitely used it, probably several times today already. We’ve only scratched the surface, but it’s really cool to see how pretty much every website I visit actually works. We haven’t had any big projects this week, because we’ve gone back to basics for the week.

Well, as usual, I’ve rambled and ranted longer than I intended to. Thanks once again for clicking, reading, not reading, ignoring, sharing, explicitly anti-sharing, or whatever you’ve done with this blog. I’m starting to like writing them, so I hope you (whoever you are) are starting to like reading them! I’ve never been good at writing conclusions (ask any of my university professors), so I’ll just end it here. THE END
