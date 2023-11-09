---
layout: text
title: "Is This Thing On?"
date: 2011-03-23
---

It's been a while. A very, very long while. So much for "writing regularly" like I told myself I would. But lo and behold, we are putting that behind us! (Or so I am telling myself, again.) I've decided that I need an outlet boring my definitively non-technical friends with ramblings of how I did this or that at some ungodly hour of the morning. And so, here we are.

### What's changed? 

Well, how I run the site has been completely overhauled. I fell in love with Tumblr, as seemingly everyone else did, but getting email notifications that the site is bouncing up and down like a ping-pong ball makes me wonder if the platform has any long-term viability. But that's a topic for far more knowledgable beings to tackle. Me? I just switched to using [Jekyll][jekyll].

The initial issue when I considering switching to Jekyll is that I use [MarsEdit][marsedit] to write up most my content. I just like the feel of a desktop application. Since Jekyll posts are all just text files, I could just launch TextMate and go to town. That doesn't really suit me though. MarsEdit has this lovely live-preview window that I've pretty much come to rely on when proof-reading on the go. At first, it seemed as though there was no possible way to hook MarsEdit into a file-based blogging system. After a helpful hint from Daniel Jalkut [on Twitter][blosxomtweet] though, I realized there was indeed a file-based blogging option and I eventually came up with a way to use this feature and leverage the power of Jekyll.

In short, all I did was customize Alex Payne's [newpost][newpostgist] script for my devious needs. What I ended up with was a new [conversion script][convertrb] that takes my text file posts from MarsEdit and spits them back out in nice Jekyll posts with the appropriate YAML data.

### The longer version

In MarsEdit, you can create a [Blosxom][blosxom] blog. This tells MarsEdit to "post" your content to text files in a directory of your choosing and optionally execute a script when you publish a new post. So, I added a _blosxom folder to my Jekyll directory and execute the aforementioned conversion script when I write a new post. Walla! MarsEdit with Jekyll. But, I couldn't stop there. 

I love the microblog layout of Tumblr. The idea of having smaller, better formatted posts for the type of content you want to share underscores the point of a blog. To share something. For many people though, that something isn't always a wall of text. So, despite the fact that I only ever use the text and link options, I needed this.

Jekyll has a wonderful template system utilizing Liquid. It renders your pages based on which layout you specify in the post metadata. So specifying a post as "link" layout allows you to specify a different template for that content. The hitch I ran into was with MarsEdit's file format. The Blosxom functionality is very bare-bones, as it was intended to be. It simply puts the title of the post on the first line, and your content follows. Expanding the conversion script and changing how I title my posts was the solution.

I now prefix all my post titles with the layout I want to use in MarsEdit. E.g. "Text: Is This Thing On?" and "Link: Amazing awesome link from twitter!" Any relevant URLs I simply include in a line at the top of the post before the actual content. When the script opens the files, it checks the post title to see if it is text or not and will additionally insert the relevant metadata and remove it from the post. Really simple, works well.

### What's so special?

Nothing, really. I'm just smitten that I can still use MarsEdit and have my site look and feel very Tumblr-esque (in fact, I copied my Tumblr theme over almost identically) and have the power of Jekyll underneath. And of course, being a Jekyll blog I am hosting it via GitHub's awesome [Pages][pages] feature.

### Shoutouts and Thank Yous

Giving credit where credit is due, I want to tip my hat to the people's work I built upon.

* [Jekyll][jekyll] is maintained by Tom Preston-Werner, Nick Quaranto, "and many awesome contributors!"
* [Alex Payne][al3xnet], for his [newpost.rb][newpostgist] script that got me wondering and for having his own personal blog open to the public [on GitHub][al3xhub]. Having a baseline to create my own was extremely helpful.
* Daniel Jalkut ([Red Sweater Software][redsweater]), for his *awesome* [MarsEdit][marsedit] application.
* GitHub, for being... well, GitHub. I host this blog there via [Pages][pages] and, of course, host the [repository][hub] there as well. They are all amazing.

[jekyll]: http://jekyllrb.com/
[marsedit]: http://www.red-sweater.com/marsedit/
[blosxomtweet]: https://twitter.com/redsweater/status/49082879086567424
[newpostgist]: https://gist.github.com/100171
[convertrb]: https://github.com/jessereadd/jessereadd.github.com/blob/master/convert.rb
[blosxom]: http://www.blosxom.com/
[pages]: http://pages.github.com/
[al3xnet]: http://al3x.net
[al3xhub]: https://github.com/al3x/al3x.github.com
[redsweater]: http://www.red-sweater.com/
[hub]: https://github.com/jessereadd/jessereadd.github.com