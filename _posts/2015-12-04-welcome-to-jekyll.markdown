---
layout: post
title:  "Adding gravatar to this site"
date:   2015-12-05 08:23:20
categories: jekyll gravatar
---

So, the first thing I do for this blog, other than adding i [Github-page][eivinhb-github] to my github user 
and creating a CNAME file with eivind.bergstol.no to make this blog available on my own domain, is to
add Gravatar to the [About](/about)-page.


Sometimes I like to be lazy. That's why I love OSS and that fact that people share code. I checked out [Gravatars
API documentation][gravatar-doc]. And thats is OK. I now know how to do it. 
But the next hit on Google was [this blog post][blog]. It's a "how to" for a Jekyll plugin 
for Gravatar. However this does not work on github-pages because it is run i -safe mode.

Using Rake at this point to build this blog and push to Github i a step too far. This was ment to be a 
simple site. Using Jekyll has kind of allready complicated this project as far as I will go for now.

{:refdef: class="round"}
![Eivind gravatar](http://www.gravatar.com/avatar/ae543005bfa33e5b2436dbab7fe460fb?45?s=25)
{: refdef}

So I hashed (MD5) my email adress into `ae543005bfa33e5b2436dbab7fe460fb` and my 
image is available on `http://www.gravatar.com/avatar/ae543005bfa33e5b2436dbab7fe460fb`

And by the way, I made the img round by using kramdown compile functionality for markdown:


{% highlight ruby %}
{:refdef: class="round"}
![Eivind gravatar](http://www.gravatar.com/avatar/ae543005bfa33e5b2436dbab7fe460fb?45?s=25)
{: refdef}
{% endhighlight %}

{% highlight css %}
.round img{
  border-radius: 50%;
}
{% endhighlight %}

[gravatar-doc]: https://en.gravatar.com/site/implement/
[eivinhb-github]:   https://github.com/eivinhb/eivinhb.github.io/    
[blog]: http://blog.sorryapp.com/blogging-with-jekyll/2014/02/13/add-author-gravatars-to-your-jekyll-site.html
