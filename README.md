Intro
-----
This is an example how to deal with hierarchical organisation of projects under Git version control.

Install
-------
 * Specify the sub-repositories in `big_hooks/post-merge` in `dir_repos` and `url_repos` variables.
 * Copy the prepared hooks to `.git/hooks`
 ```bash
 cp big_hooks/* .git/hooks  # later they will update automaticaly 
 ```
 * It is recommended to add the repository names also to `.gitignore`. See it for example
 * Run the `post-merge` hook from the "structure_big" directory
 ```bash
 ./big_hooks/post-merge
 ```

Usage
-----
 * Manually update subrepositories
 ```bash
 ./big_hooks/post-merge
 ```
 * Use the `git pull` for the "structure_big" repository. After that `git pull` is automatically applied
to the subdirectories.

Sample output of `git pull`:
```bash
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1)
Unpacking objects: 100% (3/3), done.
From https://github.com/oplatek/structure_big
   6dc4398..4164bb2  master     -> origin/master
Merge made by the 'recursive' strategy.
Cloning structure_small1 https://github.com/oplatek/structure_small1.git
~/Downloads/structure_big/structure_small1 ~/Downloads/structure_big
From https://github.com/oplatek/structure_small1
 `* branch            HEAD       -> FETCH_HEAD
Already up-to-date.
~/Downloads/structure_big
Cloning structure_small2 https://github.com/oplatek/structure_small1.git
~/Downloads/structure_big/structure_small2 ~/Downloads/structure_big
From https://github.com/oplatek/structure_small1
 * branch            HEAD       -> FETCH_HEAD
Already up-to-date.
~/Downloads/structure_big
```

If you are working in the subdirectories the commits are stored in the subdirectories.
We recommend to specify the subdirectories to `.gitignore`, which allows the "structure_big" Git repository
ignore all the changes made in the subdirectories.


Feature(Problem)
---------------

The command `git pull` trigger the recursive `git pull` for subdirectories 
only if the "main" `git fetch` (part of `git pull`) was not empty!
```bash
# In structure_big directory
$ git pull
Already up-to-date.
# does not trigger the recursive git pull for subdirectories
```

Note
----
We use two dummy Git repositories containing just README.md as example.
They can be found at:
 * [Dummy repo 1](https://github.com/oplatek/structure_small1.git)
 * [Dummy repo 2](https://github.com/oplatek/structure_small2.git)


Links
-----
[Git hooks manpage](https://www.kernel.org/pub/software/scm/git/docs/githooks.html)

