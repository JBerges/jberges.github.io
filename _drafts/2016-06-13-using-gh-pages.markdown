---
layout: post
title:  "Learning jekyll: using GitHub Pages"
date:   2016-06-13 19:20:00 +0100
categories: learn-jekyll jekyll github gh-pages
---
It's been a while since I started working on this blog, and it took a lot of time to make the decision to go on. Installing jekyll and creating the blog was one thing, publishing is another. I am using GitHub Pages to host this blog, and in this post I will explain the steps it took for me to publish a prepared jekyll website.

<!--more-->

What is GitHub Pages?
---------------------

I am not going to explain a lot, you should check this the [GitHub Pages help page](https://help.github.com/articles/what-are-github-pages/) where everything is explained.

In summary you need to create a repository with an special pattern : username.github.io (this is for user page).

After that you just need to add the jekyll page to the repository and commit it. Beware, in the case you are creating a page for a user, you will use "master" branch, if it is a page for a project, you need to use "gh-pages" branch.

Once you commit the changes, you can see the website in the url http://username.github.io. In my case it was immediate all the times that I pushed anything, so I am not sure if there is actually any delay sometimes.

Working with drafts
-------------------

First of all go to the [Working with drafts page](https://jekyllrb.com/docs/drafts/). It is quite simple, but I made a newbie error: I set a date in the future and I was not able to see the new post

Once you create the new draft in the "_drafts" folder, just execute jekyll with the --drafts option. As I am using github pages I am executing

{% highlight shell %}
$ bundle exec jekyll serve --drafts
{% endhighlight %}

Bye Bye
-------

Not a long post today, just trying to start writing on a regular basis. I am missing any command or plugin in jekyllrb to publish a draft so you don't need to change the date ...
