# Creating a post:

To get started on making a post got content/posts/ and create an md file. At the top of the post put the configuration, title, etc. Here is an example:
```
---
title: "Bridge the most complex game in the world"
date: 2022-12-12
Author: "Arnold Yang"
categories: ["Club Meet"]
summary: "Hello and welcome to our Bridge club! As a member of the club, I have to say that playing Bridge is an absolute blast. It's a game that's fun, challenging, and rewarding, and there's always something new to learn and enjoy."
weight: -1
ShowPostNavLinks: True
---
```

Then create the post in markdown: [Markdown Basic Syntax Guide](https://www.markdownguide.org/basic-syntax/)

Upload all photos to content/uploads and to add them to your post do:
```![Image title](/uploads/path-to-image)```

Afterwards, you can commit the new post and later when the website is updated the post will appear.

# How to update the website:

To start you will need install hugo: https://gohugo.io/installation/

Afterwards, clone this repository: `git clone https://github.com/PoarthanArseus/poarthanarseus.github.io`

Then, in the same directory run `hugo`

Afterwards if you can on Linux or WSL run `find . -type f -exec unix2dos {} \;`, otherwise, please wait for someone else to update the website, because the difference between unix and dos will break the website css. 

Then commit and push changes to publish them.

If you just want to see how the website looks locally, install hugo and clone then run `hugo server` and you will be able to see what the website currently looks like.
