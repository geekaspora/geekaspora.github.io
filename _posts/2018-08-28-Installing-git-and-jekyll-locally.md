--
layout: post
title: "Installing Git and Jekyll locally - part 1"
date: 2018-08-28
--
Boy, has this taken me a few days. I started on the 24th and encountered so many errors - I suspect because for some weird reason all of my files had been pushed to iCloud drive - that I closed my 1 million tabs, restarted my computer and restarted the install. Here are the steps I went through and the issues that I had to fix.

I followed the steps on [Github help](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/) 

I checked my ruby version and then tried to install bundler. I got an error about not having permissions for usr/local/bin so had to run a different piece of code:
sudo gem install bundler -n /usr/local/bin

Next up was initialising an empy repository. This failed with an error about an invalid active developer path so I tried to install xcode from the command line but realised (after assistance from a lovely colleague) that I needed to install it via the app store. 

Changing directory to my new empty repo and then creating a new branch was easy. As was creating a new Gemfile in my repo.

I went on to try to run $ bundle install. I got an error about permissions so I used my newfound trick of appending sudo (even though I'm not sure what it does) and got this warning *"Don't run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-rootusers on this machine."* which I promptly ignored because I got a lot of activity. Sadly there was an occasional smattering of "operation not permitted" feedback among the green text and I kept my fingers crossed that they wouldn't prevent the installation from being successful.

Sadly, all of that green text was a false positive so I had to rerun my bundle install using this command: **bundle install --path vendor/bundle**. 

The next (optional0 instruction said to run *"bundle exec jekyll _3.3.0_ new NEW-JEKYLL-SITE-REPOSITORY-NAME" which I thought meant a new repo instead of the previously created repo. I'd created jekyll-chimmykalu-repo before so the instruction really means use this repository. I did and got a series of lovely green text. 

I edited the gemfile as instructed and then tried to build my local jekyll site. I got an error about needing to grant write permissions to my *Gemfile.lock* file. After a lot of googling, I found a solution to this error. 
sudo chown ladmin:admin /path/Gemfile.lock

This resulted in my running jekyll locally but now I can't push. I guess I'll have to tackle that problem tomorrow.

