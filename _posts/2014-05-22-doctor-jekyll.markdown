---
layout: post
title:  "Surpise! Dr. Jekyll may have a dark side."
date:   2014-05-22
categories: dev-environment meta
---

I really appreciate the theory behind [Jekyll][jekyll]. Rather than have to contend with a cms like wordpress, and all of the security issues that come along with it, Jekyll lets you manage your content locally and then 'compile' and push a static html site to the web. I'm not sure why there aren't more platforms like it, or even similar methodologies. It's perfect for somebody like me who is, while comfortable setting up a cms and tweaking it and installing security plugins, is probably not going to remember to do regular maintence and end up being hacked by a Russian twelve-year-old. With Jekyll, twelve-year-olds be damned because the published site is just a plain old set of vanilla html files.

<!--more-->

The only issue I've had is understanding a smooth and consistent workflow. I'm using Github Pages, which basically wants to find all the site files in the *master* branch. To acheive this, I do all my editing and writing on a seperate branch called *source*, where the Jekyll engine lives. Then when it's time to publish changes, jekyll builds a static site and that gets sent to the master branch. This workflow took be a while to figure out, even after reading [a well-written explanation][deploy_steps], and emailing the author of said explanation, David Ensinger. Following his setup, when I am ready to commit my changes I do:

{% highlight ruby %}
rake commit_deploy
{% endhighlight %}

...which points to a rakefile that adds all untracked files and commits them with a timestamp, and then publishes the whole shebang. Ensinger's [rakefile][rakefile] is particularly nifty as it minifies the jekyll build that gets sent to the master branch. I haven't gotten that far yet...

[jekyll]:    http://jekyllrb.com
[deploy_steps]: http://davidensinger.com/2013/04/deploying-jekyll-to-github-pages/
[rakefile]: http://davidensinger.com/2013/07/automating-jekyll-deployment-to-github-pages-with-rake/