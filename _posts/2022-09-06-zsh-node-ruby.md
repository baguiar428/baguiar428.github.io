---
layout: post
title: ZSH Shell, Node and Ruby on Linux
subtitle: Guide to setting up Flatiron Dev Environment on Majaro Linux
cover-img: /assets/img/path.jpg
share-img: /assets/img/path.jpg
tags: [Linux, Manjaro, Arch, Shell, ZSH, Ruby, Node, Javascript]
---

This quick how-to is meant to be a guide/reference for setting up a dev environment for Flatiron school on a Linux System (Arch/Manjaro).
The major requirements are a ZSH Shell, NodeJS and Ruby (for using Gems / running tests). Neither of those come in a standard install of Manjaro.
I want to go over switching from a BASH to a ZSH shell and what that means plus how to setup NodeJS (NVM) and Ruby. There are more components to the dev environment but they are out of scope since they can be influenced by personal preference (i.e: text editor / IDE, web browser).

**ZSH Overview:**

This is actually the most complicated and significant/consequential step of setting up the Flatiron dev environment. There are many ways to approach this problem and it feels like they are hard, harder and hardest. That is because there are many levels of customization and the shell runs deep on a UNIX system. You don't have to know what it all means (I certainly don't, few people do) so this guide will focus on the simplest way to get ZSH on your system so you can look under the hood at your own pace in the future. If you walk away saying _"That was easier then he made it out to be"_ that would be a success.

Unless you do a lot of BASH scripting there won't be many differences in day-to-day usage between ZSH and BASH. There are "quality of life" improvements in ZSH that are noticeable over time, though. Like, more versatile tab completion and etc. For amore complete comparison and breakdown check out this reference (provide link for comparison).


**Installing OH-MY-ZSH via GUI**

The quickest way to install ZSH is to use Manjaro's package manager. You can search for 'oh-my-zsh' which is a framework packaged to be configured "out-of-the-box". We wouldn't be proper programmers though if we didn't give BASH a proper send off via a command-line installation.

**Installing Oh-my-ZSH via command-line / terminal**
~~~
pamac install oh-my-zsh
~~~

There are prerequisites needed for the Oh-my-ZSH framework and the package manager should handle that for you. You will be prompted to approve the install of those prerequisites, please do so. After installation you should be able to use the ZSH shell after restarting your computer (or logging off and back in again).

You can get more information on oh-my-zsh via Github: (https://github.com/ohmyzsh/ohmyzsh)

Information page for the Manjaro oh-my-zsh package: (https://software.manjaro.org/package/oh-my-zsh#!)

**Node JS (NVM) Overview:**

Node Version Manager _(NVM)_ allows you to download and install multiple versions of Node JS. It works on any POSIX-compliant shells on UNIX, MacOS and Windows WSL.

**Installing NVM via GUI**
You can use the Manjaro package manager to install NVM by searching for 'nvm'. That will install nvm along with any required dependencies.

**Installing NVM via command-line / terminal**
~~~
pamac install nvm
~~~

**Installing NVM directly from Github Repo Script**
~~~
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
~~~
or
~~~
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
~~~

You can get more information on NVM via Github: (https://github.com/nvm-sh/nvm)

Information page for the Manjaro NVM package: (https://software.manjaro.org/package/nvm#!)

**Ruby (RVM) Overview:**

Ruby Version Manager _(RVM)_ is a command-line tool which allows you to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems.
If you have the AUR repository enabled on the Manjaro package manager you can search for "rvm" and install it that way. BUT in this case, it is best to grab Ruby (RVM) directly from the source.

**Installing RVM from source via command-line / terminal**

First you will need to install the GPG key from the source. Type the following command into terminal and hit enter.
~~~
gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
~~~
Then download and install RVM with the following command in terminal. 
~~~
\curl -sSL https://get.rvm.io | bash -s stable
~~~

You can get more information on RVM via the projects webpage: (https://rvm.io/)

You can get more information on RVM via Github: (https://github.com/rvm/rvm/)

**NOTES and THOUGHTS**

Thank you for following along and I hope this post helped in some way. I was initially confused by having to move to ZSH and tried doing it manually..So that was quite the challenge and I wasn't sure how declaring BASH in the subsequent install scripts for RVM would work, but they do..So save some time and learn from my mistakes. Cheers!




