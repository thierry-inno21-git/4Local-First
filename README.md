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

 puis un nouveau cliqué sur save dan Subliem donne cela
 mbp-de-thierry:Local-First thierry-inno21$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

