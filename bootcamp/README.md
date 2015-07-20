# Rangle GIT Bootcamp

## About

This is an shortened version of our git-training course, with a focus on working with the Rangle Flow.
For more information, feel free to ask, and

* [Git Training Repository](https://github.com/rangle/git-training)
* [Rangle Flow Documentation](https://github.com/rangle/dev/tree/master/rangle-flow)

# Useful Tools

* [GitX](http://gitx.frim.nl/)
* [Hub](https://github.com/github/hub) or [Git Extras](https://github.com/tj/git-extras)
* [Git Gutter](https://github.com/jisaacks/GitGutter)

# Understanding the GIT Model

## The three states of Git

![inline](http://marklodato.github.io/visual-git-guide/basic-usage.svg.png)

Git has three states, and understanding how git interacts with these states can help make it easier to reason about working with it. The three states in Git are:

### History

History is located in the .git directory, and is where the metadata and
object database of your project is stored. This is what's copied when
you clone a repository

### Working Directory

A version of the project that is checked out and placed on disk.

Its files are pulled out of the compressed database in the .git
directory.

### Staging

A file, in the .git directory, that stores information about what will
go into your next commit.

# Branch and Fork

## Work on your own branch

(pull text over from our guidelines)
### Give branches sensible names

Branches should be descriptive of the change, and should be named to reflect if it is a fix, feature or chore. 

* git checkout -b feat-users-change-user-modal
* git checkout -b fix-users-correct-email-validation
* git checkout -b chore-add-users-to-karma-test-file

If you are using git-extras, there is a helper command called 'git create-branch' that will set the upstream for you. If you do not do this, you will need to tell git where the branch should go:

git push --set-upstream origin feat-users-change-user-modal

## Work off of forks

* Easiest way to fork is from the GitHub UI, simply click on fork
* Once forked, clone and setup the upstream
  * git clone https://github.com/e-schultz/git-training-1.git
  * git add upstream https://github.com/rangle/git-training.git

With this setup, the 'origin' is your own version of the repository, and upstream is the one that you have forked from. 

## Keep your branches in sync

Your branches and PR's should be small and short-lived, but it is still a good idea to keep them in sync with what is in master. The more often that you resync with the master branch, the less likely you will run into merge issues down the road.

You should rebase off of master frequently, but always at least before submitting a pr, and before merging a PR if you need to squash commits, or if there has been a signifigant delay between sign off and merging. 

Your 'git push' should only be going to your repository, not to the upstream master. 

To rebase a branch off of master:

* git pull --rebase upstream master

If you want to do an interactive rebase so you can also squash commits

* git checkout master
* git pull --rebase upstream master
* git checkout feat-my-branch
* git rebase master -i 


# Commits and PR practices

Make frequent commits in the course of doing your work. This makes it easy to go back. It’s ok to commit half-done work, since you will squash those commits later. But do squash (or amend) those commits before submitting a pull request (more on this below).

## Good Commits

![original](http://imgs.xkcd.com/comics/git_commit.png)
---

Do's
----
- keep commit changes as small as possible
- describe what was changed and why
- limit first line to 50 characters
- insert a blank line after first line
- wrap subsequent lines at 72 characters

Don'ts
------
- mix whitespace with functional code changes
- mix unrelated functional code changes
- send large feature in a single commit

## Squash commits before submitting a PR

You do not need to always squash a PR down to a single commit, but you should try to cut down on the 'noisy' commits that show
your work in progress/unfinished work. You should aim to have commits be 'cherry-pickable', in that if a fix is one branch - and we need that fix in another branch, we shoud be able to pick that commit and apply it else-where without needing to include other commits.

If you need to have several commits within one PR, it could be a sign that the story is too large, and/or that the PR should have been split up across multipul PRs.

Assuming that your master branch of your fork is up to date, to do an interactive rebase:


* git checkout feat-my-branch
* git rebase master -i 




