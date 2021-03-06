Intro
-----
This is an example how to deal with hierarchical organisation of projects under Git version control.

Install
-------
 * Specify the sub-repositories in `big_hooks/pull-sub` in `dir_repos` and `url_repos` variables.
 * It is recommended to add the repositories names to `.gitignore`.
 * Run the `big_hooks/register_aliases` script:

```bash
./big_hooks/register_aliases
```

   This will register the aliases `git pull-all` and `git pull-sub`.

Usage
-----
 * Update sub-repositories using `git pull-all` and `git pull-sub`.
 * `git pull-sub` will pull all sub-repositories specified in the `big_hooks/pull-sub` script.
 * `git pull-all` is an alias for `git pull ; git pull-sub`.
 * The aliases and the settings is automatically updated after merging 
   new changes from "structure_big".

Sample output of `git pull-all` from the "big_structure" directory 
```bash
$ git pull-all
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1)
Unpacking objects: 100% (3/3), done.
From https://github.com/oplatek/structure_big
   6dc4398..4164bb2  master     -> origin/master
Merge made by the 'recursive' strategy.
Pulling structure_small1 https://github.com/oplatek/structure_small1.git
~/Downloads/structure_big/structure_small1 ~/Downloads/structure_big
From https://github.com/oplatek/structure_small1
 `* branch            HEAD       -> FETCH_HEAD
Already up-to-date.
~/Downloads/structure_big
Pulling structure_small2 https://github.com/oplatek/structure_small1.git
~/Downloads/structure_big/structure_small2 ~/Downloads/structure_big
From https://github.com/oplatek/structure_small1
 * branch            HEAD       -> FETCH_HEAD
Already up-to-date.
~/Downloads/structure_big
```

Features and Gotchas
---------------

 * If you are working in the subdirectories the commits are stored in the subdirectories.
    We recommend to specify the subdirectories to `.gitignore`. 
    It allows the "structure_big" repository to ignore the changes from the subdirectories.

 * `git pull-all` and `git pull-sub` do not obviously work from within the subdirectories, 
    because they are not registered there. I find it useful, because it also notifies you 
    that you are in another working tree!

Note
----
We use two dummy Git repositories containing just README.md as example.
They can be found at:
 * [Dummy repo 1](https://github.com/oplatek/structure_small1.git)
 * [Dummy repo 2](https://github.com/oplatek/structure_small2.git)
 

License and pull request
------------------------
 * The code is released under `Apache 2.0` license.
 * Pull requests and improvements are very welcomed! All under `Apache 2.0`;-)


Links
-----
[Git hooks manpage](https://www.kernel.org/pub/software/scm/git/docs/githooks.html)

