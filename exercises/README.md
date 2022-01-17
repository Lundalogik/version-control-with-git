In this exercise, we'll take a look at cherry-picking, but we'll also take a look at some other concepts in git, like merge conflicts.

We've already looked a bit at branches, and how you can merge one branch into another.

But what if another branch has a commit you want to get into your branch, but you don't want all the other commits?

A typical example would be that someone fixed a bug in the main branch, but you still have a branch for supporting an older version of the software, and the same bug fix is needed there.

That's what `git cherry-pick` is for!

But first; we're going to encounter a merge conflict in this exercise, so let's talk a little about that.

A merge conflict happens when you are trying to add two different changes to the same file, and git can't figure out how to reconcile the differences. For example, you might be rebasing your branch onto the latest version of `main`. You've made some changes in `some-file.js`. Your changes where based on what the file looked like when you created your branch. But since then, someone else made a change to the same file, and that change is now on `main`. When you rebase your branch onto `main`, git will first remove all your commits. Then all new commits from `main` will be added. And then git will add all your commits again, one by one. But when git tries to add your commit with the change in `some-file.js`, it detects that the way the file looked before your changes doesn't match the way it looks right now.

If the two changes are made at different places in the file, git will be able to figure out what to do, and fix the problem automatically. But if the changes touched the same parts of the file, git has no way of knowing what the end result should look like. So it will pause the rebase, and tell you that you need to fix the conflict before continuing.

Merge conflicts can happen any time git is trying to "merge" two pieces of code, not only when running `git merge`. Rebasing and cherry-picking can also cause these conflicts, as well as several other operations that we won't touch on here.

When a merge conflict occurs, git will edit the file with the conflict, adding a copy of the relevant code from each of the versions, along with some lines showing what is what.

Unfortunately, the default config will not add a copy showing what the latest common version of the code looked like. But we can add that.

Run `git config --global --add merge.conflictstyle diff3`. This tells git to always show the latest common version, along with the two changed versions. The `--global` flag tells git to add this setting globally, so it works the same no matter which repo you work in. The opposite is `--local`, which tells git to only apply the setting to the repo you are currently in.

There are quite a few nice things you can do in the git config, like adding colour coding to your git output, and setting up shortcuts for commands you use a lot or tend to forget. Here are some useful settings:

    git config --global --add color.ui always
    git config --global --add color.diff always
    git config --global --add alias.praise blame
    git config --global --add alias.co checkout
    git config --global --add alias.br branch
    git config --global --add alias.s status

Now we are ready to cherry-pick a commit from another branch.

The commit we want has a bug fix for the following code:

```js
function square(x) {
    return x + x;
}
```

The fix is in the branch `exercises/cherry-picking-bugfix`. Find out which commit contains the bug fix, and cherry-pick that commit into this branch. You will get a merge conflict which you will have to resolve.

Good luck, and don't be afraid to ask for help if you need it!
