---
date: 2016-04-14
layout: post
title: Intro to Git
---

Ok, so here's what's up. Github is a website where you can manage git repositories. Git is software that allows you to track changes to your code, and is super helpful for people working together on a project. Git and github are separate things, but most people use them together. It's called Version Control, which is a term I'd never heard before, and there's options other than git (SVN and Mercurial, I think they're called). Git seems to be the most widely used though, at least in my experience.

Just a quick note, I'll link to a bunch of sweet resources at the bottom of the post, so if you don't wanna read this whole monster of a post, just check out the links at the bottom. I promise they're helpful.

First off, if you aren't comfortable using the command line to navigate your computer, I'd suggest learning how to do it. There's a graphical interface available for git, but most people use the command line. Plus you get to feel like a hacker. If you haven't used it much before, check out this tutorial: [CLI Crash Course](http://cli.learncodethehardway.org/book/). Follow the tutorial there. It's not super long, and honestly, I don't use most of what he teaches, but it was a great start. You should get comfortable moving through your directories (folders), and using the command line interface to create, move, or delete files. Git integrates really well with this.

Every project is stored in what's called a repository (repo). It's important to remember that the repository that lives on your computer is not the same as the repository that lives on Github. You have to manually sync them up, but it's simple to manage, once you figure it out. Github works by keeping the "official" version of your code on its own servers, leaving you free to mess around without worrying about breaking your production code. As you write code, you'll ```commit``` your changes on your local repository, and then ```push``` them to the remote repository when you're finished. Generally you don't need to be pushing your code every time you commit. Generally, I push at the end of the day, when I finish a particular feature/thing I'd been working on, or when someone I'm collaborating with needs to see the code I've written. The opposite of push, naturally, is ```pull```. Pulling means asking the remote repo for the most recent version of the "official" code, and adding it to your local repo.

So how do you actually do all this? The first step, if you haven't done it already, is to create an account on [github.com](https://github.com). It's free, unless you want to pay, and you should do it. Then, navigate to the directory for a project that you want to put online. From the main directory of that project, in your command line, type ```git init```. This creates a new git repo in the current directory. You can see it worked by checking to see if there's a directory within your current directory called *.git*. It's a hidden directory so you might need to do some snooping to actually see if it's there, but if you did the command line crash course linked above, you'll know what to do.

So now you've got an empty git repo in your project directory. You want to make a first commit. Simple enough. It's a good idea first to type ```git status```. This command will show you all the status (duh) of your repo. It generally lists files that it either doesn't know about, or that have changed since you last committed. If git doesn't know about the files, or they've changed since the last commit, they'll be listed in red. If git's tracking the files already, but they've changed, it'll be in green. Next, type ```git add .```. Yes, including the period. This tells git to start tracking all the files in the directory. If you want to track specific files only, you can type ```git add <filename>```, it'll select the files you tell it.

The next step is to commit those changes. Commit is kinda like saving, if that makes things clearer. So, you've done some work, added the files to git, and now you want to commit them. Any guesses how it's done? If you guessed ```git commit```, you'd be right. Well, mostly right. A commit needs a commit message. So the full command, as you'll usually write it, is ```git commit -m <enter a message here>```. If you forget to enter a commit message, you might end up in a scary black screen with some writing on it, that doesn't seem to respond to anything you do. This is a text editor called *vim*. It's pretty intense, and I won't talk about it here, but you should do some looking if you're curious. The fun thing about vim is that exiting the program is actually not at all intuitive if you've never done it before. To exit, press ```ESC```, then type ```:wq```. Escape makes sure you're in the right mode to quit, and ```:wq``` saves changes to the file and exits vim. If you make sure to remember to enter commit messages, you won't have to worry about it!

A quick note about commit messages. They should be short, concise, and informative. As I learned it, they should be a sentence, maybe two, and generally in the imperative mood, present tense. You want your messages to clearly convey what happened in that commit. "Fixed stuff", then, is a terrible message. It gives exactly 0 insight into what's happened, and is therefore entirely unhelpful to your fellow devs. "Add CSS transitions to navbar" is a much better message. Short, clear, easy to understand. There's no hard and fast rule about commit messages, but if you keep good habits, you'll make other people around you happy.

If your commit messages are short and to the point, it makes sense that you should be committing often. Generally, you want each commit to refer to one change to the code. So try to get into the habit of committing often. If nothing else, it'll make your Github look good!

Finally, we're done working for the day, and so we're ready to push our code to the remote repo. If you've sensed the pattern by now, you'll guess that the command is ```git push```, or more fully, ```git push origin master```. Don't worry too much for now about what ```origin``` and ```master``` are, but they'll be important for more advanced git stuff. Basically, ```origin``` refers to a particular remote repo, and ```master``` means you're pushing to the main branch, which is something I'll try and cover later on. You may have to enter your github name and password, which will determine whether you have access to that particular repo, and it'll push your local commits to the github repo.

Seems easy right? No? Well yeah, it's a bit weird at first. But trust me, once you get used to it, it becomes natural and you'll understand why it's so useful to commit frequently and to write good commit messages.

Here's a short version of the workflow, great if you've got completed projects you want to showcase on github.

1. Create an account on github, and link it to your computer. Follow the Github Setup Guide linked below, it'll tell you all about HTTPS and SSH and stuff that I'm not gonna talk about.
2. Navigate to the root directory of your project using the command line, and type ```git init```.
3. Begin tracking the entire project with git, using ```git add .```.
4. Commit the project in it's current state with ```git commit -m <message>```.
5. Push the project to Github with ```git push origin master```.
6. Revel in your github skills as the job offers pour in!


###Links

- [CLI Crash Course](http://cli.learncodethehardway.org/book/)
- [Atlassian Git Articles](https://www.atlassian.com/git/tutorials/what-is-version-control)
- [Github Setup Guide](https://www.atlassian.com/git/tutorials/what-is-version-control)
- [My Personal Github Page](https://github.com/bowmanmike)
