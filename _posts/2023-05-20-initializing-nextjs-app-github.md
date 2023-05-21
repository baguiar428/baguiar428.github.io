---
layout: post
title: Creating a NextJS Project and adding it to Github
subtitle: Guide to creating a NextJS Project with Tailwind and adding it to Github
cover-img: /assets/img/nextjs-logo.svg
share-img: /assets/img/nextjs_logo.png
tags: [Javascript, Yarn, NextJS, Github, Tailwind CSS]
---

As usual, I like to document my boilerplate templates but this particular entry is especially useful to me (and hopefully for you, as well). I've been using NextJS and when I would add a local repo to Github i'd get a "Large files detected." error that ended with:
~~~
 ! [rejected]        main -> main (pre-receive hook declined)
error: failed to push some refs to 'github.com:baguiar428/*Your Github Repo *'
~~~

After clueing in on the specific offending file in the error message I saw that it was related to Yarn. We have to figure out a way to exclude the troublesome file that gets generated when we create the NextJS project. But is it "safe" to remove the file?
After digging around through Yarn documentation I found [Q&A - Which files should be gitignored](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored).
That was really useful information but even after adding the entries to my .gitignore I still got the same error. The issue was a conflict in Git with the repo I created via the Github website and the Git configuration generated locally when using Yarn. I tried using [Github documentation for managing large files](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github) but that didn't work because the remote repo wasn't connected to the local one to begin with. I think it is related to conflicting HEAD entries but I haven't demystified all of the Github voodoo yet.
Even though Yarn doesn't allow for generating a project without initializing Git, that I know of, there is a simple way to resolve this issue..Generate your project, delete your local .git, edit your .gitignore then reinitialize git. Let's see what that looks like step by step.





