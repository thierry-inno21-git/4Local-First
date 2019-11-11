# quelques lignes de commandes pour sortir d'un situation de conflit en master local et remote
Installation de mergetool et instruction d'utilisation sur stackoverflow
Try: git mergetool

It opens a GUI that steps 
you through each conflict, and you get to choose how to merge. Sometimes it requires a bit of hand editing afterwards, but usually it's enough by itself. It is much better than doing the whole thing by hand certainly.

As per @JoshGlover comment:

The command doesn't necessarily open a GUI unless you install one. Running git mergetool for me resulted in vimdiff being used. You can install one of the following tools to use it instead: meld, opendiff, kdiff3, tkdiff, xxdiff, tortoisemerge, gvimdiff, diffuse, ecmerge, p4merge, araxis, vimdiff, emerge.

Below is the sample procedure to use vimdiff for resolve merge conflicts. Based on this link

Step 1: Run following commands in your terminal

git config merge.tool vimdiff
git config merge.conflictstyle diff3
git config mergetool.prompt false
This will set vimdiff as the default merge tool.

Step 2: Run following command in terminal

git mergetool
Step 3: You will see a vimdiff display in following format

  ╔═══════╦══════╦════════╗
  ║       ║      ║        ║
  ║ LOCAL ║ BASE ║ REMOTE ║
  ║       ║      ║        ║
  ╠═══════╩══════╩════════╣
  ║                       ║
  ║        MERGED         ║
  ║                       ║
  ╚═══════════════════════╝
These 4 views are

LOCAL – this is file from the current branch

BASE – common ancestor, how file looked before both changes

REMOTE – file you are merging into your branch

MERGED – merge result, this is what gets saved in the repo
You can navigate among these views using ctrl+w. You can directly reach MERGED view using ctrl+w followed by j.

More info about vimdiff navigation here and here

Step 4. You could edit the MERGED view the following way

If you want to get changes from REMOTE

:diffg RE  
If you want to get changes from BASE

:diffg BA  
If you want to get changes from LOCAL

:diffg LO 
Step 5. Save, Exit, Commit and Clean up

:wqa save and exit from vi

git commit -m "message"


# Lignes de commandes pour revenir à une synchro normale

```
mbp-de-thierry:Local-First thierry-inno21$ ls
README.md	app.js
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git pull origin master
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 9 (delta 3), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (9/9), done.
From https://github.com/thierry-inno21-git/4Local-First
 * branch            master     -> FETCH_HEAD
   ed68e44..ade6c76  master     -> origin/master
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
mbp-de-thierry:Local-First thierry-inno21$ git config merge.tool vimdiff
mbp-de-thierry:Local-First thierry-inno21$ git config merge.conflictstyle diff3
mbp-de-thierry:Local-First thierry-inno21$ git config mergetool.prompt false
mbp-de-thierry:Local-First thierry-inno21$ git mergetool
Merging:
README.md

Normal merge conflict for 'README.md':
  {local}: modified file
  {remote}: modified file
4 files to edit
mbp-de-thierry:Local-First thierry-inno21$ git commit -m "un merge grace à la magie de mergetool"
[master 598c2c1] un merge grace à la magie de mergetool
mbp-de-thierry:Local-First thierry-inno21$ git clean
fatal: clean.requireForce defaults to true and neither -i, -n, nor -f given; refusing to clean
mbp-de-thierry:Local-First thierry-inno21$ ls
README.md	README.md.orig	app.js
mbp-de-thierry:Local-First thierry-inno21$ git pull origin master
From https://github.com/thierry-inno21-git/4Local-First
 * branch            master     -> FETCH_HEAD
Already up to date.
mbp-de-thierry:Local-First thierry-inno21$ git checkout master
Already on 'master'
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md.orig

nothing added to commit but untracked files present (use "git add" to track)
mbp-de-thierry:Local-First thierry-inno21$ nano README.md.orig 
mbp-de-thierry:Local-First thierry-inno21$ git add README.md.orig 
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   README.md.orig

mbp-de-thierry:Local-First thierry-inno21$ git commit -m "commit post mergetool de readme.md.orig"
[master ae80fe7] commit post mergetool de readme.md.orig
 1 file changed, 278 insertions(+)
 create mode 100644 README.md.orig
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 5 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git pull origin master
From https://github.com/thierry-inno21-git/4Local-First
 * branch            master     -> FETCH_HEAD
Already up to date.
mbp-de-thierry:Local-First thierry-inno21$ git branch -d branch
error: branch 'branch' not found.
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 5 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ ls
README.md	README.md.orig	app.js
mbp-de-thierry:Local-First thierry-inno21$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/thierry-inno21-git/4Local-First
 * branch            master     -> FETCH_HEAD
   ade6c76..6fb0481  master     -> origin/master
Merge made by the 'recursive' strategy.
 app.js | 1 +
 1 file changed, 1 insertion(+)
```