---
layout: post
title:  Freezing and Thawing Git State
date:   2013-12-11 17:07:53 -0400
categories: development
tags:
  - git
  - shell
---

We do lightening/dev talks every week at work, where a few developers get up and talk about cool projects or anything they think is interesting. One of the recent talks by [James Macauley] was about git freeze and git thaw.

The basic idea is that git stash kinda sucks sometimes. To show that, let's run through an example.

## Example of Using Git Stash

    $ mkdir demo_repo && cd demo_repo
    $ git init
    $ git commit -m "initial commit" --allow-empty
    $ touch README.md
    $ touch LICENSE
    $ git add README.md

Now if we run `git status`, we should see the following:

<div class="blk-bg">
  <img src="/public/img/git_status_001.png" alt="git status">
</div>

If we now stash our changes and get the status, we'll see that LICENSE is still untracked.

    $ git stash
    $ git status

<div class="blk-bg">
  <img src="/public/img/git_status_002.png" alt="git status">
</div>

This is intentional. As a rule, git will not do anything with files it's not tracking. This comes in handy for things like password files (arguably should be git ignored) and other files that don't belong in git.

However, there are times when you want to take the current state of your working directory and stash it. And when you `pop` the stash you want everything to go back to the way it was.

Luckily, git will convert any executable file in your path to a custom command. All we need to do it call it `git-<command>` and voila!

## Git Freeze and Git Thaw

The goal of git freeze is to create two commits: `WIP [STAGED]` and `WIP [UNSTANGED]` containing the staged and unstages files respectively.

These scripts were developed by [James Macauley]. You can check out the original gist [here](https://gist.github.com/jamesmacaulay/582757).

{% gist 7922871 git-freeze %}

Thaw reverses the process by resetting `HEAD` appropriately.

{% gist 7922871 git-thaw %}

Both scripts take care to only create/revert commits if they're needed.

## Making It Work

These scripts should be placed in a directory in your `$PATH`. __*Make sure to make them executable.*__

Going back to our `demo_repo` example from earlier, let's pop that stash.

    $ git stash pop

You should see this again:

<div class="blk-bg">
  <img src="/public/img/git_status_001.png" alt="git status">
</div>

Now we can run `git freeze` to uh..._freeze_ the current state. And `git thaw` to thaw it out again.

[James Macauley]: //about.me/jamesmacaulay
