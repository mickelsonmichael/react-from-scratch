# React from Scratch

Welcome! This will be a tutorial to help you (and me) learn how to creation an application in React **from scratch**. You may be wondering why you even want to create a React application from scratch when tools like `create-react-app` exist and make creating an application a breeze. Well, the answer is you wouldn't; nine times out of ten you will just use some template like the `create-react-app` command to build your application and get programming right away. The benefit to creating the app from scratch is the knowledge gained along the way.

If you rely on `create-react-app` entirely and never make any modifications to the pre-populated files and configurations, then it will be all the more difficult to make those modifications _later_ in the application's lifespan, since you won't deeply understand where the configurations are located, what options you need to change, and what those effects may be.

Thus, the focus of this guide is on helping you understand the ins-and-outs of React, Babel, and Webpack. I'll also do my best to provide some additional tips on Git. Throughout the tutorial, you will (ideally) be able to follow along with my build process simply by viewing the commit history. I will make the best effort to keep the commit history algined with the progress of this README file, so you can view the process step-by-step, commit-by-commit.

Finally, the ulterior motive behind this tutorial is to better teach _myself_ these concepts. I am by no means a React expert. I started programming in React earlier this year and have made a random assortment of apps in various degrees of complexity, with each (hopefully) being better built than the last. By the end of this tutorial, I hope both you and I are better developers from it.

If you're an experienced React developer and you come across this, please feel free to read through or follow along, and if you notice any issues, please create a pull request and correct the misstep! As a community we can create the greatest version of this tutorial that we can.

## Brief

The "goal" of this application will be to create a simple one-person Black Jack game. If you don't know the rules of Black Jack, you can read them anywhere online or at [Bicycle's website](https://bicyclecards.com/how-to-play/blackjack/). Essentially, we have a deck of 52 cards and the goal of the player is to get as close to 21 points (2 being 2 points, 7 being 7 points, etc.) as possible. The rules of the game aren't particularly important, since by the time we get to implementing those, we will have already passed the core concepts we need to cover. But, in my opinion it is worth having an end goal in mind from the start. It will lead to a better process in the end.

What you should have installed:

- NodeJS (and npm)
- Git
- A shell (this can be Git Bash, WSL, Terminal, PowerShell, or whatever you are most comfortable with)

If you aren't already comfortable with a shell, then you _should_ be. I know you can get by just fine without it, I did for years, but I truly believe the main advantage to using shells isn't the script-ability or control you get, but the deeper understanding you get from running the commands yourself. By using Git in the command line you gain a deeper understanding of what your GUI utilities are doing in the background. Plus, it's going to be pretty difficult finding good GUI applications for `npm`.

If you need a shell for Windows (Mac and Linux users have a great one already built in), then I'd recommend Git Bash; if you have installed Git to your machine already (which you should before you start this tutorial), then it is likely already installed on your machine. Just launch the application using the start menu and it will be well configured already. This is a great starting point for most developers; it is easy to set up, and the commands are _mostly_ the same as Linux. If you are looking to get more advanced, check out Windows Subsystem for Linux, it is essentially a Linux machine running in your Windows machine like a little Russian doll, and so far I have nothing but good things to say about it. However, it does come with a little more overhead of installation than Git Bash.

## Part 1: Setting Up Our Repository

This will be one of the more brief chapters, since I will make a lot of assumptions about your prior knowledge here. There are a few things I will stress that may seem simple to many people, but I have found myself glancing over them in the past.

To start off, we need to create the Git repository that we will be tracking our changes. By now, I have already created the repository on my local machine, but I will walk you through the general steps now.

First step of the journey, create a directory to store our repository and enter it

```bash
mkdir react-from-scratch
cd react-from-scratch
```

Next, we'll initialize our Git repository using the simple command `git init`. This will create the necessary .git directory and begin tracking our changes. At this point, if you were to try to run the command `git push`, Git would complain that there is no upstream repository to push to; this is because we haven't configured one yet. Go to your favorite Git management site (GitHub, Bitbucket, GitLab, etc.) and create a repository. Then, you can run the commands to add a repository

```bash
git remote add origin {url-to-repo}
git fetch
git checkout {main/master}
```

The first command can be broken down into three parts; `git remote` narrows down our git command to the "remote" management section of our Git repo. You can have multiple remote repositories, but it's generally uncommon. Most of the time you will have a single remote, which by convention is named "origin". Thus that's what the next part of the command is doing, `add origin`. We are telling git to add a remote repository and name it origin. Finally, the last part will be the URL to repository; this URL is generally located by clicking a "Clone" button somewhere on your site.

Second, we'll fetch the current branches from that remote repository. This is mainly just to get the `main` or `master` branch (GitHub recently changed its default branch name to `main` instead of `master`. You can read more about that decision [here](https://github.com/github/renaming/) here) so we can seamlessly push our changes to it without having any conflicts. We'll ensure we are on that branch by running the last command `git checkout main`, which will ensure all our new changes are made on the `main` branch. Normally, you'd want to make you changes on a separate branch every time, or at least on a `dev` branch of some sort, but since this is a demo application, we'll stick with `main` for our convenience.

Finally, to wrap up our Git configuration, we'll create a `.gitignore` file and add a few entires to it:

```bash
touch .gitignore
```

We can stop there for now. Add your changes using `git add .`, then commit them using `git commit -m "Message goes here"`. I won't list these commands again, from here on out I'll just say "commit our changes".

