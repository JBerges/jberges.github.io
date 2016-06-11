---
layout: post
title:  "Learning jekyll: installation with a virtual machine"
date:   2015-12-29 12:43:54 +0100
categories: learn-jekyll jekyll
---
This is the first post of a series, a hope a long one, where I will explain how to use Jekyll. I will write as I learn Jekyll, I hope this will help to newcomers like me. In my case I decided to use a virtual machine (VirtualBox) for the ruby, gem manager and jekyll software. This way I could try the technology without polluting my computer.

If you are willing to learn jekyll, try it a bit and see what happens next without installing all the stuff in your daily computer, you can use my way of installing jekyll.

<!--more-->

The easy and painful way
------------------------

First of all, where do I start? This is quite easy: [Go to official Jekyll page](http://jekyllrb.com/). To install jekyll you will just need to install ruby from the official pacakge. Just 5 minutes and you're done, so why bother with any other thing?

Well, I have been doing this with more technologies that you can think: webservers, php, drupal, joomla, ruby on rails, java frameworks, android sdk ... After some years trying things you end up with your computer full of stuff that you don't want, or worse, that you want and need but you need to install again when you clean your computer.

The solution: install every new technology in a virtual machine.

Installing a virtual machine
----------------------------

There are multiple solution for virtual machines, I am using VirtualBox - not going to explain why, just is the one that works for me, if you have other options do not hesitate to used them. Check the installation details in [VirtualBox official page](https://www.virtualbox.org/).

Once it is installed, the interesting part starts. Which Operating System are you going to use as guest? Think about this carefully as you should use the most practical for you. I decided to go for an installation without graphical interface to make it light and fast to start. Another interesting thing is to create a clone once the OS is installed in the virtual machine. With this, you can start a new machine skipping the OS installation.

In my case I am using Ubuntu Server 14.04. I am installing to most basic stuff: ssh server is the only must for this post. In the installation you need to take care of the user, this will be called later in this post as #GUEST_USER#.

Network configuration and helpers
---------------------------------

And now, you need to make this work easy from your host machine. The idea is that you will start your virtual machine and edit from your host. In order to make this easy, we will install something in your host (ok, we are installing stuff in the host, but it is really small amount).

The first step is to run the virtual machine like another computer in the same network, so you can access using an ip with the same network than your host machine. This will let you : connect via ssh and access the web server from the browser.

To configure the network, go to virtualBox, select your machine, and click in configuration. Go to "network" section and select bridged mode. For more info check the [Official VirtualBox network documentation](https://www.virtualbox.org/manual/ch06.html). After this, start you virtual machine and configure it to use an static ip (this ip will be names as #GUEST_IP# later). For more info check [Official Ubuntu Server network configuration web](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic).

Once your virtual machine is accessible from your host via ssh (check with command "ssh #GUEST_IP#"), we will install [sshfs](https://github.com/libfuse/sshfs) to mount the virtual box folder as a remote one. Just type this:

{% highlight shell %}
$ sudo apt-get install sshfs
{% endhighlight %}

Then, you need to mount the folder when you want to work with Jekyll.Create a new folder with your selected path (I will use #HOST_MOUNT_FOLDER#, please change to your value):
{% highlight shell %}
$ mkdir #HOST_MOUNT_FOLDER#
{% endhighlight %}

Create a new file and put this:

{% highlight shell %}
#!/bin/sh
sshfs -o idmap=user #GUEST_USER#@#GUEST_IP#:/home/your_user_home_in_guest #HOST_MOUNT_FOLDER#
{% endhighlight %}

Installing Jekyll
-----------------
So, now everything is prepared. Just do the 5 minutes installation that is needed to install jekyll:

{% highlight shell %}
$ sudo apt-get install ruby-full
$ gem install jekyll
{% endhighlight %}

Easy, isn't it?

Conclusion
----------

Now you have a virtualBox machine that can be used for jekyll development, that can be cloned to be used as a different environment machine, can be moved to another host and is not polluting your main computer.

On next posts I will talk about my first steps using jekyll and my editors and extra configurations. I hope this post was useful.
