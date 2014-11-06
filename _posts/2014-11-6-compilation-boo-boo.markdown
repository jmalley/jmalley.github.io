---
layout: post
title:  "Compilation boo boo"
date:   2014-11-6 14:16:16
categories: deployment rails
---

There's a distinct shift in the work required when moving from development to deployment. Making an app in Rails requires a little googling but mostly logic and tinkering. When it's time to share your baby with the world, however, logic doesn't come along. Deployments require practice, domain knowledge, and patience. There is no way to think your way to replicating best practices. You have to look everything up. Such was my frustration today when trying to get the [Asset Pipeline][assetpipe] to work in a brand new production environment.
<!--more-->
First came the dreaded transition from sqlite to postgres. I'm not sure why I don't always start with a pg rails project, seeing as virtually all of the cloud rails hosts like heroku and ninefold require it. That move includes troubleshooting the SQL statements that postgres deems not explicit enough.

Next comes a frustrating problem and, as most frustrating problems are in the end, a fairly obvious one. My app deployed like a charm but for some reason some assets, specifically images, on S3 were getting access denied errors. Wut. It ended up being because in my .scss stylesheet, I was saying:

{% highlight css %}
background: url('background.png')
{% endhighlight %}

I needed to be using the image-url tag instead of the url one. It's subtle, but sass and rails won't attach the fingerprinting that comes along with pre-compilation if you don't use the special tag. That took me 3 hours to figure out because I thought it was some S3 error first.

I'm pretty happy with my setup now, though. Every time I push to my [bitbucket][bitbucket] repo, [ninefold][ninefold] redeploys my app automatically. Very nice for a lightweight app.


[assetpipe]: http://guides.rubyonrails.org/asset_pipeline.html#how-to-use-the-asset-pipeline
[bitbucket]: http://bitbucket.org
[ninefold]:	 http://ninefold.com/
