# Practical Git for Everyday Professional Use (Egghead)
---


###How to convert a folder into a git repo?
```
cd <your_folder>

git init
```

Do 'ls -a' and you will see an empty .git folder inside it.

###How to remove git from a folder?

```
cd <your_folder>

rm -rf .git/
```

This removes git folder, which contains all the git info, from our project.

###How to set up a remote on a repo?
```
git remote add origin <my_repo_url.git>
```

You get a git url when you create a new repo on GitHub (or bitbucket).

To verify the addition, type `git remote -v`

###How to copy remote repos to local machine?
```
git clone <my_git_url>

E.g. git clone https://github.com/trevordmiller/utility-functions.git
```

###How to check for any changes in files?
```
git status
```

###How to stage all the changes you made in a repo?
```
git add -A
```

###How to commit changes lying in stage?
```
git commit -m "my message"
```
This will commit all the changes.


###How to sync all the commited changes from local to remote repo?
```
git push
```
###How to sync all the new changes from remote to local repo?
```
git pull
```

###git pull is shortcut for which two commands?
```
git fetch // fetch all the changes, but don't include
git merge // include fetched changes
```

###How to create a new branch?
```
git branch <branch_name>
```
Do `git branch` to view all our branches.

###How to switch to a new branch?
```
git checkout <branch_name>
```

###How to create a new branch and checkout into it in single command?

```
git checkout -b <my_second_branch>
```

###How to sync two branches?
First checkout the branch that you want to combine the feature into. Let's say we have developed a new feature into new-feature branch and want to merge it to master. So first we need to checkout master. After that we need to run git merge.

```
git checkout master
git merge new-feature
```

Git automatically determines the right algorithm to merge.

###How to delete a branch?
```
git branch -d <branch-name>
```

###How to save uncommitted changes?
First stage the changes and then run git stash.
```
git add -A
git stash
```

Now when you come back, do `git stash apply` to bring your old file.

```
git stash apply
```

###How to see commit history?
```
git log
```

###What are the various arguments that can be passed to git log?
```
git log --oneline //condensing commits to a single line
git log --decorate //shows references
git log --graph //displays branch structure of each commit
git log -p //shows patches(changes)
git log --stat //shows number of insertons and deletions
```
Above commands can also be composed(combined together).

###How to filter commit history in git log?
```
git log -4 // shows only last 4 commits
git log --after="yesterday" //shows commits that happened after yesterday
git log --after="3/15/16" --before="yesterday" //shows commits b/w March 15th and yesterday
git log --author="Vikas" //filters commits to only authors that have "Vikas" in their name. Can also parse regex
git log --grep="string_to_search" //searches commit messages with that string
git log -p -S"Math" //search for string inside code changes. Using -p (for patch) to format logs accordingly. Will show commits wherever Math was involved.
git log -i --author="Vikas" //will show commits by vikas as well. i flag makes it case insensitive. 
git log <file_name_1> <file_name_2> //shows commits specific to only the listed files.
```

###How to see specific changes made in files since last commit?
```
git diff
```
Three + or - means file. Single + or - means a line of code.

To see differences in condensed way, do:

```
git diff --stat
```

Default references are working directory and last commit.

###How to change references for git diff?
```
git diff --cached //diff b/w working directory and staged area
git diff HEAD //to see all changes since last commit (both in working directory and staging area)
```

###How to check changes before pushing to remote master?
```
git fetch //fetches changes
git diff origin/master //shows new changes before you push
```

To check diff in a single file, do:

```
git diff origin/master <file_name> //shows new changes before you push
```

###How to see who made a particular change in a file?
```
git blame <file_name>
```

###How to add version numbers to a commit?
```
git tag v1.2.3
git push --tags //push tags to remote repo
git tag -a v1.2.3 -m "message" //to push anotated tags. If you leave message part, it will open editor to let you write more detailed notes.
```

###How to add aliases to our gitconfig?
```
git config --global alias.graph 'log --graph --oneline'
```

To run above command, just do `git graph` (`git <alias_name>`, which in our case is graph).

Run `git config --list` to see your git config file.

###How to ignore some files from git?
- Include their name in .gitignore file.
- To ignore an already tracked file, run: `git rm --cached`


###How to ignore some files globally?
Create a global gitignore file and add it to .gitconfig.

E.g. After adding .gitignore_global file to root, do this:

```
git config --global core.excludesfile ~/.gitignore_global
```