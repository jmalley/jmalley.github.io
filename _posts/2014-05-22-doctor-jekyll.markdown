---
layout: post
title:  "Surpise! Dr. Jekyll may have a dark side."
date:   2014-05-22
categories: dev-environment meta
---

I really appreciate the theory behind [Jekyll][jekyll]. Rather than have to contend with a cms like wordpress, and all of the security issues that come along with it, Jekyll lets you manage your content locally and then 'compile' and push a static html site to the web. I'm not sure why there aren't more platforms like it, or even similar methodologies. It's perfect for somebody like me who is, while comfortable setting up a cms and tweaking it and installing security plugins, is probably not going to remember to do regular maintence and end up being hacked by a Russian twelve-year-old. With Jekyll, twelve-year-olds be damned because the published site is just a plain old set of vanilla html files.

<!-- more -->

The only issue I've had is understanding a smooth and consistent workflow. I'm using Github Pages, which basically wants to find all the site files in the *master* branch. To acheive this, I do all my editing and writing on a seperate branch called *source*. When I am ready to update the site:

{% highlight ruby %}
$ jekyll build
$ git add --all
$ git commit -m "I've made great changes."
$ publish_website
{% endhighlight %}

That last little nugget is an alias I set up in .bashrc that fires off the following commands I [found online][deploy_steps] (it took me far too long to figure out I couldn't chain together commands in gitconfig, and that this is the proper place to do it):

{% highlight ruby %}

alias publish_website="git push; git branch -D master; git checkout -b master; git filter-branch --subdirectory-filter _site/ -f; git checkout source; git push --all origin --force"

{% endhighlight ruby %}

The gist of it is that we want the master to contain the site files, while we want source to contain the jekyll engine and everything else. Is it *perfect*? No. The important thing is it works for now. In the future I will try to set up a [rakefile for this][rakefile], but I'd like the wait until I know what a rakefile is.


[jekyll]:    http://jekyllrb.com
[deploy_steps]: http://davidensinger.com/2013/04/deploying-jekyll-to-github-pages/
[rakefile]: http://davidensinger.com/2013/07/automating-jekyll-deployment-to-github-pages-with-rake/