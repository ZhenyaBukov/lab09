$ export GITHUB_USERNAME=ZhenyaBukov
$ export GITHUB_EMAIL=zhenya.bukov.06@mail.ru
$ export GITHUB_TOKEN=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
$ alias edit=nano


$ cd ${GITHUB_USERNAME}/workspace
$ workspace % source scripts/activate


$ workspace % mkdir ~/.config
mkdir: /Users/zhenya/.config: File exists
$ workspace % cat > ~/.config/hub <<EOF
heredoc> github.com:
heredoc> - user: ${GITHUB_USERNAME}
heredoc> oauth_token: ${GITHUB_TOKEN}
heredoc> protocol: ssh  
heredoc> EOF
$ workspace % git config --global hub.protocol https
fatal: bad config line 1 in file /Users/zhenya/.gitconfig
$ workspace % git config --global
fatal: bad config line 1 in file /Users/zhenya/.gitconfig
$ workspace % cat .gitconfig
cat: .gitconfig: No such file or directory
$ workspace % git config --global
fatal: bad config line 1 in file /Users/zhenya/.gitconfig
$ workspace % vim /Users/zhenya/.gitconfig 
$ workspace % git config --global         
usage: git config [<options>]

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    --worktree            use per-worktree config file
    -f, --file <file>     use given config file
    --blob <blob-id>      read config from given blob object

Action
    --get                 get value: name [value-pattern]
    --get-all             get all values: key [value-pattern]
    --get-regexp          get values for regexp: name-regex [value-pattern]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value-pattern]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-pattern]
    --unset-all           remove all matches: name [value-pattern]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    --fixed-value         use string equality when comparing values to 'value-pattern'
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    -t, --type <type>     value is given this type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
    --bool-or-str         value is --bool or string
    --path                value is a path (file or directory name)
    --expiry-date         value is an expiry date

Other
    -z, --null            terminate values with NUL byte
    --name-only           show variable names only
    --includes            respect include directives on lookup
    --show-origin         show origin of config (file, standard input, blob, command line)
    --show-scope          show scope of config (worktree, local, global, system, command)
    --default <value>     with --get, use default value when missing entry

    

$ workspace % mkdir projects/lab02 && cd projects/lab02
mkdir: projects/lab02: File exists
$ workspace % git init
Reinitialized existing Git repository in /Users/zhenya/ZhenyaBukov/workspace/.git/
$ workspace % git config --global user.name ${GITHUB_USERNAME}
$ workspace % git config --global user.email ${GITHUB_EMAIL}
$ workspace % git config -e --global
$ workspace % git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git 
error: remote origin already exists.
$ workspace % git pull origin main  
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 2.59 KiB | 530.00 KiB/s, done.
From https://github.com/ZhenyaBukov/lab02
 * branch            main       -> FETCH_HEAD
   9ace567..44121d8  main       -> origin/main
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint: 
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint: 
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
fatal: Need to specify how to reconcile divergent branches.
$ workspace % touch README.md
$ workspace % git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.DS_Store
	node/
	projects/
	scripts/

nothing added to commit but untracked files present (use "git add" to track)
$ workspace % git log
commit 3b4b3e950b4abd1bd3485bfae01944dbc8078d8c (HEAD -> main)
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Apr 4 06:17:44 2025 -0700

    added README.md

commit 9ace56709a316017f673d021a927a442257136ef
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Mon Mar 24 11:17:24 2025 -0700

    Create .gitignore

commit f445772d1cc42ee7e87fa8f738271b0c1af4234b
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Mar 7 03:46:53 2025 -0800

    Initial commit
$ workspace % git add README.md
$ workspace % git commit -m"added REAME.md"
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.DS_Store
	node/
	projects/
	scripts/

nothing added to commit but untracked files present (use "git add" to track)
$ workspace % git push origin main  
Username for 'https://github.com': ZhenyaBukov
Password for 'https://ZhenyaBukov@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/ZhenyaBukov/lab02.git/'
$ workspace % vim /Users/zhenya/.gitconfig                                        
$ workspace % git push origin main                                                 
Username for 'https://github.com': ZhenyaBukov
Password for 'https://ZhenyaBukov@github.com': 
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/ZhenyaBukov/lab02.git/'
$ workspace % vim .git/config        
$ workspace % vim ~/.config
$ workspace % vim ~/.config/hub 
$ workspace % git remote add origin git@github.com:ZhenyaBukov/lab02.git           
error: remote origin already exists.
$ workspace % git remote remove origin
$ workspace % git remote add origin git@github.com:ZhenyaBukov/lab02.git
$ workspace % git push origin main                                      
To github.com:ZhenyaBukov/lab02.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'github.com:ZhenyaBukov/lab02.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
$ workspace % git pull
From github.com:ZhenyaBukov/lab02
 * [new branch]      main       -> origin/main
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> main

$ workspace % git log
commit 3b4b3e950b4abd1bd3485bfae01944dbc8078d8c (HEAD -> main)
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Apr 4 06:17:44 2025 -0700

    added README.md

commit 9ace56709a316017f673d021a927a442257136ef
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Mon Mar 24 11:17:24 2025 -0700

    Create .gitignore

commit f445772d1cc42ee7e87fa8f738271b0c1af4234b
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Mar 7 03:46:53 2025 -0800

    Initial commit
$ workspace % git push -f origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 318 bytes | 318.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:ZhenyaBukov/lab02.git
 + 44121d8...3b4b3e9 main -> main (forced update)
$ workspace % git push origin main     
Everything up-to-date


$ workspace % git pull origin main  
From github.com:ZhenyaBukov/lab02
 * branch            main       -> FETCH_HEAD
Already up to date.
$ workspace % git log
commit 3b4b3e950b4abd1bd3485bfae01944dbc8078d8c (HEAD -> main, origin/main)
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Apr 4 06:17:44 2025 -0700

    added README.md

commit 9ace56709a316017f673d021a927a442257136ef
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Mon Mar 24 11:17:24 2025 -0700

    Create .gitignore

commit f445772d1cc42ee7e87fa8f738271b0c1af4234b
Author: ZhenyaBukov <zhenya.bukov.06@mail.ru>
Date:   Fri Mar 7 03:46:53 2025 -0800

    Initial commit

    
$ workspace % mkdir sources
$ workspace % mkdir include
$ workspace % mkdir examples
$ workspace % cat > sources/print.cpp <<EOF
heredoc> #include <print.hpp>
heredoc> #include <print.hpp>                                  

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF


$ workspace % cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF


$ workspace % cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF


$ workspace % cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF


$ workspace % edit README.md


$ workspace % git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.DS_Store
	examples/
	include/
	node/
	projects/
	scripts/
	sources/

nothing added to commit but untracked files present (use "git add" to track)
$ workspace % git add .
warning: adding embedded git repository: projects/lab02
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint: 
hint: 	git submodule add <url> projects/lab02
hint: 
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint: 
hint: 	git rm --cached projects/lab02
hint: 
hint: See "git help submodule" for more information.
$ workspace % git commit -m"added sources"
[main 87ac8ff] added sources
 2757 files changed, 338351 insertions(+)
$ workspace % git push origin main  
Enumerating objects: 2925, done.
Counting objects: 100% (2925/2925), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2754/2754), done.
Writing objects: 100% (2924/2924), 13.44 MiB | 1.24 MiB/s, done.
Total 2924 (delta 519), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (519/519), done.
To github.com:ZhenyaBukov/lab02.git
   3b4b3e9..87ac8ff  main -> main
