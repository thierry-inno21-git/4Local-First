Test de la création d'un repopsitory local

Création d'un repository git
git init Local-First

Ajout avec Sublime Text d'un fichier source JavaScript app.js

utilisation du tuto du site https://rogerdudler.github.io/git-guide/index.fr.html

après la création du repository il faut y ajouter des fichier via git (sinon git ne voit pas les fichiers qui sont ajouté dans le dossier qu'il surveille)

mbp-de-thierry:Local-First thierry-inno21$ ls
app.js

git add *

mbp-de-thierry:Local-First thierry-inno21$ git commit -m "OK pour valider cette premiere verson de app.js"
[master (root-commit) c59a3dc] OK pour valider cette premiere verson de app.js
 1 file changed, 14 insertions(+)
 create mode 100644 app.js

 mbp-de-thierry:Local-First thierry-inno21$ git show
commit c59a3dca3c08e84c4eff4eff79a293bc1fd21105 (HEAD -> master)
Author: ThierryAdmin <15143935+thierry-inno21-git@users.noreply.github.com>
Date:   Sun Nov 10 16:35:28 2019 +0100

    OK pour valider cette premiere verson de app.js

diff --git a/app.js b/app.js
new file mode 100644
index 0000000..3161f41
--- /dev/null
+++ b/app.js
@@ -0,0 +1,14 @@
+const http = require('http');
+
+const hostname = '127.0.0.1';
+const port = 3000;
+
+const server = http.createServer((req, res) => {
+  res.statusCode = 200;
+  res.setHeader('Content-Type', 'text/plain');
+  res.end('Hello World\n');
+});
+


mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)

Now stage the newly added file README.md

mbp-de-thierry:Local-First thierry-inno21$ git add README.md 
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   README.md

On voit bien le nouveau fichier

mbp-de-thierry:Local-First thierry-inno21$ git commit -m "now second commit to treat well mister README.md"
[master 0b60728] now second commit to treat well mister README.md
 1 file changed, 61 insertions(+)
 create mode 100644 README.md

 puis un nouveau cliqué sur save dan Sublime donne cela
 mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

mbp-de-thierry:Local-First thierry-inno21$ git commit -a
Aborting commit due to empty commit message.
mbp-de-thierry:Local-First thierry-inno21$ git commit -a -m"troisième commit pour prendre en compte les dernieres saisies"
[master f8cf038] troisième commit pour prendre en compte les dernieres saisies
 1 file changed, 23 insertions(+)
mbp-de-thierry:Local-First thierry-inno21$ git branch
* master
mbp-de-thierry:Local-First thierry-inno21$ git checkout -b chapitre2README
Switched to a new branch 'chapitre2README'
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch chapitre2README
nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch chapitre2README
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
mbp-de-thierry:Local-First thierry-inno21$ git branch
* chapitre2README
  master
mbp-de-thierry:Local-First thierry-inno21$ git branch master
fatal: A branch named 'master' already exists.
mbp-de-thierry:Local-First thierry-inno21$ git checkout master
M	README.md
Switched to branch 'master'
mbp-de-thierry:Local-First thierry-inno21$ git branch
  chapitre2README
* master
mbp-de-thierry:Local-First thierry-inno21$ git remote add origin https://github.com/thierry-inno21-git/4Local-First.git
mbp-de-thierry:Local-First thierry-inno21$ git push -u origin master
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 2.09 KiB | 2.09 MiB/s, done.
Total 9 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/thierry-inno21-git/4Local-First.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
mbp-de-thierry:Local-First thierry-inno21$ git commit -a -m "on a maintenant une version du master en remote" 
[master 58779b2] on a maintenant une version du master en remote
 1 file changed, 45 insertions(+)
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git branch
  chapitre2README
* master
mbp-de-thierry:Local-First thierry-inno21$ git push origin chapitre2README
Total 0 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'chapitre2README' on GitHub by visiting:
remote:      https://github.com/thierry-inno21-git/4Local-First/pull/new/chapitre2README
remote: 
To https://github.com/thierry-inno21-git/4Local-First.git
 * [new branch]      chapitre2README -> chapitre2README
mbp-de-thierry:Local-First thierry-inno21$ git commit -a -m "on ajoute le chapitre suivant post creation branche dans github"
[master b30d980] on ajoute le chapitre suivant post creation branche dans github
 1 file changed, 16 insertions(+)
mbp-de-thierry:Local-First thierry-inno21$ git branch
  chapitre2README
* master
mbp-de-thierry:Local-First thierry-inno21$ git checkout chapitre2README
Switched to branch 'chapitre2README'
mbp-de-thierry:Local-First thierry-inno21$ git branch
* chapitre2README
  master
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch chapitre2README
nothing to commit, working tree clean
mbp-de-thierry:Local-First thierry-inno21$ git status
On branch chapitre2README
nothing to commit, working tree clean

just adding m five cents
