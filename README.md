Intro
-----
The repository is a proposal how to deal hierarchical organisation of projects in Git

Install
-------
 * Specify the sub-repositories in `big_hooks/post-merge` in `dir_repos` and `url_repos` variables.
 * Copy the prepared hooks to `.git/hooks`
 ```bash
 cp big_hooks/* .git/hooks  # later they will update automaticaly 
 ```
 * It is recommended to add the repository names also to `.gitignore`. See it for example

