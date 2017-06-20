# Github Cheatsheet
This assumes that you already know how Git works. I've written down how to do a few of the things that I do over and over again. Feel free to add your own / update the existing instructions.

Adding a branch to my repository, based on a remote repository:
---------------------------------------------------------------
```
git fetch https://github.com/drivechain-project/mainchain
git checkout -b upstream FETCH_HEAD
git push -u origin upstream
```

Updating a branch in my repository, from an upstream repository:
--------------------------------------------------------------
```
git fetch
git checkout fees  // the branch I want to update
git fetch https://github.com/drivechain-project/sidechain
git merge FETCH_HEAD fees
git push -u origin fees
```

Create a new branch, from an existing branch in my repository:
--------------------------------------------------------------
```
git checkout -b newbranch existingbranch
```

Amend a new commit into the last one, for a fix:
------------------------------------------------
```
git add .
git commit --amend
git push -u --force origin nolibm
```

Checkout a commit from a repository into a new local branch:
------------------------------------------------------------
```
git fetch https://github.com/bitcoin/bitcoin 18c1325dcdb2eb2f2119bd558c111ed439038cc6:newBranch
```

Rebase a pull request:
----------------------
```
git remote add upstream https://github.com/bitcoin/bitcoin
git fetch upstream
squash if you want to:
git rebase -i HEAD~nCommitsToSquash
git push -u origin rebase
```

Cleanup a bunch of commits:
---------------------------
Make a branch based on the branch you want to cleanup with the sha256 of the commit before you started adding things.

```
git fetch https://github.com/bitcoin/bitcoin sha256:newBranch
```

upload the branch

```
git push -u origin newbranch
```

Go on to github and make a pull request from the old branch with the changes, into the new branch before the changes.

Use github.com to squash and merge
