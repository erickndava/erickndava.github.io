---
layout: post
title: Installing Octopress on Windows 7 for Blogging on GitHub
date: 2015-03-17T03:42:24+02:00
summary:    Setting the stage for blogging.
categories: tutorial technical
thumbnail: flask
tags:
 - hands-on
 - work
---
Having a working Octopress install on Windows 7 was not straightforward
for me. This post outlines the steps I would recommend to have a working
environment.

**Important:** There are upcoming changes to the whole of the Octopress
‘platform’ so please [readup](http://octopress.org/), but while we wait
…

#### **Step 0:** **Pre-Requisite:**

To have the environment going, you’ll need to have
[git](http://git-scm.com/) up and running. But to save yourself the
tears setting up SSH and permission stuff, I recommend you download and
install [Github for Windows](https://windows.github.com/). This will
provide you with a ‘reliable’ command line interface. The correct paths
for applications readily setup for you.

#### **Step 1:** **Install Ruby**

My working environment used the installer, [Ruby
1.9.3-p194](https://www.dropbox.com/s/bxgyqxlpcqwwgkw/rubyinstaller-1.9.3-p194.exe?dl=0)
(*This might be an outdated version but it works well*). Download and
install the package, be sure to tick the check-boxes as shown in the
image below (*This will save you “command not found” errors later on*)
![Ruby Install](/images/ruby_install_options.png "Ruby Installation")

#### **Step 2:** **Install The Development Kit**

Download
[DevKit-tdm-32-4.5.2-20111229-1559-sfx](https://www.dropbox.com/s/41iw9xscb7lxrqa/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe?dl=0)
and extract this to C:/RubyDevKit.

#### **Step 3:** **Create/ Choose Your Repositories Folder.**

Create a folder, something like c:/github. In here we’ll store the files
and folders which make up our blog, configuration files, posts, images,
etc.

#### **Step 4:** **Setting Up The Environment At The Command Line**

![Git Shell](/images/GitShell.png "Command Line") Now, using the Git
Shell that was co-installed when you installed GitHub for Windows, run
the following command:

```
$ cd c:/RubyDevKit
$ ruby dk.rb init
$ ruby dk.rb install
```

Thats should have the Ruby environment setup for you. Now continue with:

```
$ cd ..
$ cd c:/github          
$ git clone git://github.com/imathis/octopress.git yourusername.github.io
```

This clones the octopress repository. Now open the folder you cloned
Octopress to, viz yourusername.github.io. Locate the **Gemfile** and
using a text editor (I use Notepad++), open the file, replacing
**https** with **http**. **This is important!**

Now do:

```
$ cd c:/github/yourusername.github.io
$ gem install bundler
$ bundle install
```

If, after everything is done the word error does not appear on the
command line, you’re good to go. Still on the command line, continue
with:

```
$ rake install
```

This installs the default Octopress theme. I wanted a different
[theme](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes),
Justin-Kelly-Theme in particular, so had to run:

```
$ git clone https://github.com/wallace/justin-kelly-theme.git ./themes/justin-kelly-theme
$ rake install['justin-kelly-theme']
```

#### **Step 5:** **Setting Up A Repository on GitHub**

You probably already have a GitHub account. Logon to GitHub and create a
repository **yourusername.github.io**. Never mind the must have README
suggestion by GitHub. Copy your SSH clone URL to a text editor or
clipboard. It is similar to
*git@github.com:yourusername/youruserame.github.io.git* and you can see
it when you visit your newly created repository. So you should now be
having
[https://github.com/yourusername/yourusername.github.io](https://github.com/yourusername/yourusername.github.io**)

Go back to the command line and run:

```
$ rake setup_github_pages
```
You will be prompted for a url: type
*git@github.com:yourusername/youruserame.github.io.git*

You can then continue on the command line with:

```
$ rake generate
$ rake deploy
```
Opening [http://youruserame.github.io](http://youruserame.github.io) in
your browser should land you at your sparkling new blog, albeit, without
content.

Now it’s time for some content creation.

The [Octopress Website](http://octopress.org) has excellent
documentation to get you started. So head over there and get blogging.

#### Extras

After several tweaks to my blogging environment, I added a sidebar
twitter widget, Comments via Disqus and Search(*Currently in the
works*), to have a more appealing blog. Tutorials to do this are
ubiquitous on the web and since i didn’t struggle setting them up I saw
no need to include the howto with this post. I Include references below
for quick access.

-   The go to [Reference for Octopress](http://octopress.org/docs/)
-   Details of the [Justin Kelly
    Theme](http://blog.justin.kelly.org.au/octopress-theme/)
-   An alternative [Step by Step Setup
    Instruction](http://www.techelex.org/setup-octopress-windows7/)
-   Another alternative [Setup
    Instructions](http://jtdp.github.io/blog/2013/04/23/installing-octopress-on-windows-7/)
-   Twitter Feeds - [An Octopress Twitter
    Asides](http://raisedadead.com/octopress-twitter-aside/)

#### “ Parting Quote ”

[@erickndava](https://twitter.com/erickndava), March 2015

> If the problem is IT related in whatever manner, and you can’t seem to
> find the solution, it’s probably on the internet - you just have to
> google harder for it.

#### \#postscript

#### \> Murky waters. *(tl;dr)*

After I had initially setup my environment according to the procedure
outlined above, at somepoint evrything just broke. (*could have been
some Windows update*)I lost my debut post. Tried to setup again using,
[Jekyll on Windows](http://jekyllrb.com/docs/windows/). That too had me
in circles of troubleshoot. So I did the whole thing over, following the
procedure here and Voila! I’m back in business.

#### Why another guide?

-   In the event my current environment goes awry, I will have a
    reference should I need to start over.
-   This is a deliberate move to force myself to document stuff - the
    usual thing for me is once I have it working successfully, I
    continue, ‘storing’ the procedure/ methodology.

-   [Git](http://git-scm.com/) vs [GitHub for
    Windows](https://windows.github.com/) - Initially I installed git
    and attempted through command line to set up SSH keys and all. That
    had me in circles troubleshooting. I must say there is great
    documentation out there so a novice can start with git. Since my
    current objective was to *BLOG!* I decided to quit the git-command
    line route and installed GitHub for Windows. What a breeze! (*I am
    planning to deepen my knowledge of git so planning on even using
    [GitEye](http://www.collab.net/products/giteye) for its graphic cues
    to git commands*)

#### [Wordpress](https://wordpress.com/), [Medium](https://medium.com/about/welcome-to-medium-9e53ca408c48), [Tumblr](https://www.flickr.com/get_the_most.gne#blog)…Anyone?

I chose Octopress and blogging on GitHub over other ‘easier’ methods for
a few reasons:

-   This becomes my gentle introduction to git and GitHub
-   I like to be in ‘control’, viz I enjoy seeing cogs of a technology/
    implementation moving.

