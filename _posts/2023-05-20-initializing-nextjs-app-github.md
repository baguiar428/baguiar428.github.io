---
layout: post
title: Creating a NextJS + Tailwind Project with Yarn and adding it to Github
subtitle: Guide to creating a NextJS Project with Yarn and resolving filesize limitations when adding project to Github
cover-img: /assets/img/nextjs-logo.svg
share-img: /assets/img/nextjs_logo.png
tags: [Javascript, Yarn, NextJS, Github, Tailwind CSS]
---

As usual, I like to document my boilerplate templates but this particular entry is especially useful to me (and hopefully for you, as well). I've been using NextJS and when I would add a local repo to Github i'd get a "Large files detected." error that ended with:
~~~
 ! [rejected]        main -> main (pre-receive hook declined)
error: failed to push some refs to 'github.com:*Your Github Repo*'
~~~

After clueing in on the specific offending file in the error message I saw that it was related to Yarn. We have to figure out a way to exclude the troublesome file that gets generated when we create the NextJS project. But is it "safe" to remove the file?
After digging around through Yarn documentation I found [Q&A - Which files should be gitignored](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored).
That was really useful information but even after adding the entries to my .gitignore I still got the same error. The issue was a conflict in Git with the repo I created via the Github website and the Git configuration generated locally when using Yarn. I tried using [Github documentation for managing large files](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github) but that didn't work because the remote repo wasn't connected to the local one to begin with. I think it is related to conflicting HEAD entries but I haven't demystified all of the Github voodoo yet.
Even though Yarn doesn't allow for generating a project without initializing Git, that I know of, there is a simple way to resolve this issue..Generate your project, delete your local .git, edit your .gitignore then reinitialize git. Let's see what that looks like step by step.

**Step 1: Creating a NextJS Project**<br>
Change into the directory you want to save your project
then create your project with the following command:
~~~
yarn create next-app
~~~
When you run the command you will receive a series of prompts on how you'd like to configure your project. One of the prompts will let you set up Tailwind out-of-the-box, how awesome is that! I've included the prompts below for reference but the defaults are generally safe.
~~~
✔ What is your project named? … test
✔ Would you like to use TypeScript with this project? … No / Yes
✔ Would you like to use ESLint with this project? … No / Yes
✔ Would you like to use Tailwind CSS with this project? … No / Yes
✔ Would you like to use `src/` directory with this project? … No / Yes
✔ Use App Router (recommended)? … No / Yes
✔ Would you like to customize the default import alias? … No / Yes
Creating a new Next.js app in /home/hyperion/Development/next.js_projects/test.
~~~

**Step 2: Deleting the auto-generated Git Config**<br>
Once your project is created you will need to change directory into it. When you're in the directory if you list out all the files you should see a .git folder. Go ahead and delete the whole folder. Note that the preceding dot in .git means the folder is hidden.
In *unix (Linux and Mac) system you would do the following 3 commands to complete this step:
~~~
$ cd your_project_folder
$ ls -al
$ rm -rf .git
~~~

**Step 3: Editing the .gitignore file**<br>
Now we need to edit the .gitignore file so that it knows which folders/files Git should ignore. This is a very useful feature and critical for excluding unnecessary files from syncing with Git, for example, files used for local cache purposes. Usint the information from the Yarn documentation I added the last entry in the file. In this case, I used the rules for "zero-install".
~~~
# See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# next.js
/.next/
/out/

# production
/build

# misc
.DS_Store
*.pem

# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# local env files
.env*.local

# vercel
.vercel

# typescript
*.tsbuildinfo
next-env.d.ts

# yarn zero-install
.yarn/*
!.yarn/cache
!.yarn/patches
!.yarn/plugins
!.yarn/releases
!.yarn/sdks
!.yarn/versions
~~~

**Step 4: Create Repo on github.com**<br>
After you create your repo on github.com you will get a screen with setup commands to run on your local machine.
One of the sections is labeled as **…or create a new repository on the command line**.
We will be using a slightly modified version of that series of commands. Instead of adding a README file we will be adding the .gitignore file.
~~~
git init
git add .gitignore
git commit -m "Configuring Yarn Zero-Install"
git branch -M main
git remote add origin git@github.com:*Your Github Repo*
git push -u origin main
~~~
When you refresh your browser you will see that your Github repo has been initialized with your .gitignore file.

**Step 5: Adding the rest of your project to your repo**<br>
Now that your .gitignore has been configured you can add the rest of your project and it won't crash out with any pesky errors. You would proceed as you normally would:
~~~
$ git add .
$ git commit -m 'Adding NextJS Project'
$ git push
~~~
Now when you refresh your browser you will see that your repo has synced.


**Final Thoughts**
This workflow can apply to many more situations and working with .gitignore will almost certainly come up in every developers journey. I hope this guide helped you learn how to use .gitignore.<br>

**Happy Coding**






