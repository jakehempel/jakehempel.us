---
title: Little Bash Trick to Help Me Keep on Top of Tasks
layout: projects
categories: projects
---
This is just a little bash trick I use to help keep me keep track of tasks.

<!--more-->

With my final semester of university being as busy as it is, I needed a way to keep on top of all of my tasks and due-dates. I use my laptop for most of my daily school tasks, so it's only natural that it should also be used to help me organize my daily tasks.

I'm not, however, a fan of most of the 'sticky note' desktop widgets that I used to use for the same purpose; I feel like they're somewhat obnoxious and gets in the way of the windows I'm working in. I needed a subtler, yet just as effective way of making sure I'm constantly reminded of what I have to do.

I then decided to ponder what the 'Linux' way of accomplishing this task would be. I tried using a simple 'todo.txt' file sitting on my desktop to keep track of my daily tasks, but it would have the opposite problem of the sticky note widgets was was _too_ subtle and I'd often forget it existed while it was buried under all of the windows I was working in.

I arrived then at my current solution. I added this simple block of bash into my .bashrc:

```bash
if [ -s /home/jake/Desktop/todo.txt ]
then
        ( echo -e "TODO:\n" ; cat /home/vintar/Desktop/todo ) | cowsay -n
else
        fortune | cowsay
fi    
```

Every time I open up a new terminal window, it reads the todo.txt file on my desktop. If it's file size is larger than zero -- or it has any text in it -- it will pipe out its' contents into cowsay to make it look classy. If there's nothing in the file, it will just output the afformentioned cow telling my my fortune. Since I'm typically using the command line interface for most of my Linux needs, I see this quite often and it isn't too intrusive in my workflow and I can easily add or remove tasks from this file.

Here's an idea of what the output looks like:

![Cow Task List](/assets/img/cowtask.png)


Here's a photo of the cow giving my words of wisdom:

![Cow Wisdom](/assets/img/cowwisdom.png)
