---
layout: post
title: Migrating from Blogger to Jekyll + GitHub Pages
tags:
- tech
- technology
- internet
---
After getting back from Shanghai in 2016, my blog sort of died and with good reason: I
was kind of embarrassed about what it looked like. Having started this blog in 2005, I chose to 
host it on Blogger, which at the time, seemed like a great choice. There was a WYSIWYG editor, 
I didn't need to bother too much about formatting, and in 2005, I only needed to think about 
making it look good on desktop. It was the perfect option to use to keep in touch with friends and
family when I first moved abroad. 

This is what it looked like up to now:

**Desktop**

![What Blogger looked like on desktop](/assets/img/blogger-desktop.png)

**Mobile**

![What Blogger looked like on mobile](/assets/img/blogger-mobile.png)

Fugly, right? The look and feel are downright outdated. There isn't a responsive version of the blog, but 
instead a mobile web version. The tools and admin area on Blogger feel like they haven't been updated since
Google bought the platform in 2003. It's like it's the unwanted, ugly side project from Google that makes
Google+ look useful.

<h3>The migration from Blogger</h3>

After getting back from China, I had some time and attempted to migrate my blog to using [Jekyll](https://jekyllrb.com/){:target="_blank"}
and [GitHub Pages](https://pages.github.com/){:target="_blank"} because I wanted to have more control over my entire site.
I [read the documentation on migrating](https://import.jekyllrb.com/docs/blogger/){:target="_blank"} and it seemed
easy enough. Long story short, I was unsuccessful migrating because I got frustrated setting up the
dev environment and trying to get Ruby to work.

Fast forward to the beginning of December 2018. Looking to reassure myself that I do indeed know 
what I'm doing and I *can* handle my own website, I tried again. 

Thanks to lots of googling, I figured out why Ruby didn't work back in 2016: I needed to update Ruby 
to be able to work with Jekyll. So simple, yet it didn't occur to me two years ago. 
[This page](http://codingpad.maryspad.com/2017/04/29/update-mac-os-x-to-the-current-version-of-ruby/){:target="_blank"}
explained it in crystal clear language that someone like me, who has no knowledge of Ruby or even really 
using Terminal, could understand with easy-to-follow instructions how to do it.

Next, I read [this well-written guide](http://jmcglone.com/guides/github-pages/){:target="_blank"} with another set of 
easy instructions about how everything works. I also watched the [entire series from Mike Dane](https://www.mikedane.com/static-site-generators/jekyll/){:target="_blank"} 
on using Jekyll while working on my actual site, which was probably the most helpful tool I came across. 
Mike Dane's videos were more helpful than the series I had found back in 2016, so credit is definitely due here. 

Surprisingly, the actual migration from Blogger to GitHub Pages was really quick in terms of content. 
But after that, I had to deal with these issues:

* Redirects from links with the Blogger URL, and not my domain name;
* Migrating all images;
* Fixing formatting, spacing, and styling;
* Moving my domain name from Blogger to GitHub Pages;

It may not seem a lot, but when digging down into these issues, it turned out to be a big pile of garbage.

<h3>Redirects and setting the right links</h3>
I thought this would be easy and tried to figure out how to run a script to do it, but failed. Looking into some of the HTML files,
I discovered that Blogger changed the original URL to a different TLD when I moved from the US to Germany 
back in 2005. That meant it changed from boondoxgarage.blogspot.com to boondoxgarage.blogspot.de, making links inconsistent,
which was probably the smallest of problems. More annoyingly, it left *some* of the links with the Blogger URLs, 
but then changed some of them to my own domain when I added it in 2015. This was the most minor issue 
and probably could've been changed easily by doing a search + replace in multiple files with TextWrangler 
(equivalent of Notepad++ that I use on my Mac). I fixed this bit easily.

<h3>Migrating images</h3>

This was annoying because of several factors:

1. I had split hosting my images between [my Flickr account](https://www.flickr.com/photos/sannielee/){:target="_blank"} and uploading them directly to Blogger;
2. The images hosted on Blogger were scattered between different URLs;
3. Not all images that I uploaded to Blogger were in the ZIP file I downloaded for whatever reason, nor 
can I find them anywhere in my Google Photos account;
4. Flickr's business model is changing and I need to get them off Flickr before they disappear into 
oblivion or I need to pay to keep them there.

Unfortunately, I couldn't just run a script or do a search + replace function since all of the URLs for the 
images were completely different. Here, I wound up going through the 106 blog posts and manually looking at if I had to download the 
images off Flickr or find them in the bowels of Blogger/Google Photos, adjusting the links, and getting rid of a lot of the extraneous attributes that Blogger
added. I'm not quite done with styling the images, but I decided by removing the attributes,
it will make it easier for me to adjust everything nicely using CSS later. It still looks better than 
having various sizes or weird, unnecessary tables to display the images.

It drove me insane that I split hosting the images in different locations. Having worked on several websites 
professionally, I wanted to smack the 2005 me and say what a terrible idea this is for so many reasons. But
getting them all in one place will definitely make things easier moving forward. You live, you learn.

<h3>Formatting, spacing, and styling</h3>

Fixing the formatting, spacing, and styling was by far the biggest pain in the ass. Basically, this was
my reaction:

<p>
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">There is so much garbage HTML in my migrated blog posts. Blogger sucks. so. much. <a href="https://t.co/2OSEZnyb3A">pic.twitter.com/2OSEZnyb3A</a></p>&mdash; P. Sannie Lee (@geekrockchick24) <a href="https://twitter.com/geekrockchick24/status/1078717128281337856?ref_src=twsrc%5Etfw">December 28, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</p>

Blogger is seriously a pile of trash. It might've been great in 2005, but when looking at the random garbage
that it added for **no reason whatsoever**, it made me so mad. Even beginners learning how to write HTML
wouldn't write whatever the heck was exported in the XML file from Blogger! There was no consistency whatsoever&mdash;
paragraphs were divided up using various methods: `<br />`, `<span>`, `<div>`, and on occasion `<p>`. There
was lots of random attributes, tags that were useless (for example, `<h3></h3>` with no text between the two tags or
lots of `<br />` were added and looked terrible).

I tried running a Ruby script I had found [outlined and linked in this blog post](https://www.ybrikman.com/writing/2015/04/20/migrating-from-blogger-to-github-pages/){:target="_blank"} to fix it,
but I didn't have the permissions to run it. I googled how to change the permissions, tried to do it, and
failed. Rather than getting frustrated and then having to do a manual cleanup anyway according to the author of that post,
I decided to just manually change everything since that was probably faster and more accurate. 
To say the least, the majority of the manual work was split between images and cleaning up the markup.

<h3>Moving my domain name from Blogger to GitHub Pages</h3>

The final step of moving my domain name from Blogger to GitHub Pages was fairly straightforward, though as always,
there were some minor issues. After changing the URL from my GitHub.io URL to my own domain, the CSS went missing after 
pushing to production. It looked fine locally, so after looking around online, I started playing around with the `_config.yml` file.
Nobody had really explained the difference between `baseurl` and `url` in all the guides I mentioned above, 
but [this short explanation](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/){:target="_blank"}
gave me enough information that I figured it had to be that. Basically, because I have my own domain, I don't need the
`baseurl` and just need to add the URL in the field `url`. After fixing this and pushing to production, everything looked fine.

The last point was to build a redirect on my old Blogger site by adding a piece of Javascript into the `<head>`, which I adjusted
off the site [here](http://rharriso.github.io/2016/02/01/redirecting-blogspot-posts-to-jekyll.html){:target="_blank"}. That way
if anyone happened upon my old pages, they would automatically be redirected to my new site.

<h3>Wrapping up</h3>

After all that, my blog was migrated from Blogger to GitHub Pages using Jekyll. In the spirit of working agile, my MVP of migrating my blog is done 🎉🎉🎉 and, true to being the product owner that I am,
I've set up a kanban board on [Trello](https://trello.com/){:target="_blank"} with some improvements, features, and bugs. And yes, I've prioritized it accordingly. But
the best thing about migrating my blog is having more control over my own site and having a better understanding of how things
work on a website. 

One last note: I've changed the name of this blog twice since 2005. Originally "Boondox Garage" because of living in Vermont (the "boondox" 
there, spelled like that for no particular reason) and the Weezer song *"In the Garage,"* I changed it to "Expat Hoch Zwei" (translated
to Expat Squared) when I moved to China. Both of these names make no sense now because I'm not in Vermont and I'm not an expat squared.
(Besides which, I'm an [immigrant as I pointed out once before](/2015/04/19/differences-between-expats-immigrants.html){:target="_blank"}).
To bring things full circle, I've gone back to the idea of "*In the Garage*" since the stuff I write about is
such a mixed bag of things. And this likely won't change.