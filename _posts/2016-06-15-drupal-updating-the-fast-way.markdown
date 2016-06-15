---
layout: post
title:  "Drupal: updating (the fast way)"
date:   2016-06-15 12:43:54 +0100
categories: drupal drupal7
---
I have some Drupal sites online from a past time where I was developing in Drupal. They are nothing special, but anyway you need to keep up-to-date to avoid security issues. I have to confess that updating Drupal is probably the only thing that I really hated back in time, and at some point I had to find a way to do it secure and fast.

This is my fast track of a Drupal update ...

<!--more-->

1. Go to maintenance mode in admin/config/development/maintenance
2. Set all cache to off in admin/config/development/performance
3. Clear all caches in the same page admin/config/development/performance
4. Do a backup of your database (do it now, not before, to avoid having a lot of cached data)
5. Do a backup of the files : sites/ folder and sub-folders, and .htaccess file
6. Download the new version of drupal (remove sites/ folder)
7. Create a new folder in your hosting and copy new drupal + sites + profiles + .htaccess (in this order)
8. Rename your old folder to a .backup and rename the folder created in previous step to the folder that domain is pointing
9. Go to update.php and do the update process (if you cannot access check point six of [Update procedure in Drupal 7](https://www.drupal.org/node/2700991))
10. If everything goes ok then you can continue, if not, fall back to backup (rename folder + restore backed up database)
11. Clear all caches in admin/config/development/performance
12. Set all cache on in the same page admin/config/development/performance
11. Go back to online mode in admin/config/development/maintenance

About the folder thing
----------------------

The steps 7 and 8 are a total custom thing that I am doing to go faster in case of restoring when anything goes wrong. The idea is that in my hosting I have multiple domains, pointing each of them to a folder.

My hosting allows me to rename the folder that a domain is pointing, which makes the domain to stop working. By preparing everything and renaming I can switch between versions really fast.

If your hosting doesn't allow this, think at least a way of moving all the files without using an FTP application.
