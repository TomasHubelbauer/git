# Git

## Set up

https://github.com/tomasHubelbauer/git-config

## Pull With Submodules

`git config --global submodule.recurse true`

[Stack Overflow answer](https://stackoverflow.com/a/49427199/2715716)

## Delete file with its history

https://stackoverflow.com/a/872700/2715716

Implemented in https://github.com/TomasHubelbauer/git-erase

## Delete file's history keeping its current version

```sh
# Remove file with its history from the local repository
git filter-branch --force --index-filter "git rm --ignore-unmatch name.ext" --prune-empty HEAD

# Restore file's latest version from the remote repository
git checkout origin/main -- name.ext
```

`git checkout` can't work from the local repository, because in it, after the
history was rewritten, the file never existed, so it has nowhere it could be
recovered from. For that reason, it needs to be recovered from the remote copy
where the new history has not been forced-pushed into yet, so the file still
exists there.

Example: https://github.com/TomasHubelbauer/tomashubelbauer
