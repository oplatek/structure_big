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

Usage
-----
Use the common `git pull` for the "structure_big" repository, `git pull` is automatically applied
to the subdirectories.

If you are working in the subdirectories the commits are stored in the subdirectories.
We recommend to specify the subdirectories to `.gitignore`, which allows the "structure_big" Git repository
ignore all the changes made in the subdirectories.


*Problem*
```bash
$ git pull
Already up-to-date.
# does not trigger the recursive git pull
```

Note
----
We use two dummy Git repositories containing just README.md as example.
They can be found at:
 * [Dummy repo 01](https://github.com/oplatek/structure_small01.git)
 * [Dummy repo 02](https://github.com/oplatek/structure_small2.git)


Links
-----
[Git hooks manpage](https://www.kernel.org/pub/software/scm/git/docs/githooks.html)

