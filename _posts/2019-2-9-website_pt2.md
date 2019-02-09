---
title: Making of this Website, part 2
layout: projects
categories: projects
---

I have made more process on this site since the [last post](/projects/2018/11/09/website_pt1.html) I had written. At this stage, I feel like it is ready to be shown on the Internet.

<!--more-->

Since last post I have settled on some design and layout decisions that I was formerly unsure of. I had chosen initially to use some degree of jQuery to make the home page look a bit flashier, but decided that was too superfluous. The button functionality was cute, but having the website front page links clearly listed out clearly in columns looked overall cleaner and fit the minimalist aesthetic I'm going for. What can I say? I was excited to apply some of the new jQuery magic I had learned

![front page](/assets/img/frontpage2-9-19.png "Front Page"){:height="70%" width="70%"}

On the back end of things, I have been experimenting with the way I deploy and manage this website. An important part of maintaining  to my own personal blog like this is the work-flow associated with editing and contributing to it. I had tried to centralize all development onto the web server this site is being hosted on, meaning every time I wanted to edit or add to the site I had to remotely connect to the server and directly edit. While keeping development isolated in one location was a tidy way of keeping all associated files in one place, this brought up two problems: editing the site while I was offline/away from home was impossible, and exposing myself to data loss if the hard drive holding the website data had failed for whatever reason.

After considering various alternatives, GitHub turned out to be the most viable answer for these issues. Migrating the development to a GitHub repository allows me to write blog posts offline from any device with the latest version and serves as off-site cloud-storage for all of the files in case of failure. Before this project I only had cursory experience using GitHub for classes, and decided that this was a good of an excuse as any to really learn to develop with GitHub. To streamline the deployment process, I wrote a basic Bash script to be ran on the web server that will: pull the latest version from the repository, build the site locally, and using rsync to synchronize Jekyll's output to the web directory.

I had attempted to automate this process by making a crontab entry for the script. GitHub requires credentials for every pull request, which is problematic since I wanted this to be fully automated. There are options for GitHub to store user credentials locally, but that turned out to be *even more* problematic when it stored my credentials in plain text. That's right, **plain text**, a cardinal sin for anyone concerned with information security. For a lack of better alternatives, deploying my site manually is the only viable option.

Overall, I am pleased with the current state of my site so far after seeing it evolve from a few bare-bones HTML pages. It's almost like my baby in that way, seeing it grow up into the state it is now. It's by no means finished though; rather I hope to make this website a project I progressively add to throughout my life as a means of having my own independent presence on the web where I can articulate my thoughts. I still want to add more to it so it can be more mature before I begin indexing it in search engines. 
