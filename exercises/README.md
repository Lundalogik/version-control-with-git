Welcome to the commit exercises!

Well, staging and committing really. And some other stuff. But I wanted to keep the branch name short.

So, we've already done some basic staging and committing, but this is where I'll try to show you why staging isn't just an unnecessary and time wasting step, but really something very useful.

Everybody has their own way of working when they're writing code, and if you don't happen to be some kind of wizard that has everything figured out exactly before you even touch the keyboard, git can likely help you out with your development process.

Whether you like to commit your changes after every keystroke, or work for weeks before committing anything, git can be very useful for sorting your changes into chunks of related changes. Doing so is helpful in many ways. It helps your teammates get an overview of the changes you made, and helps them understand which changes are connected and which are separate. It can help them, you, and anyone else understand what changes were made and why back in September last year. And it makes your changes easy to apply to a different version of the software, perhaps as a patch-release for an older version that you still need to support.

We'll get into how you pick separate changes later, but for now, let's focus on how we can split a bunch of different changes into separate commits.

Below is some simple javascript:

```js
function createTardis() {
    var doorOpen = false;

    var currentCamouflage = 'Police Public Call Box';


    return {
        openDoor: openDoor,
        closeDoor: closeDoor,
        getCurrentCamo: getCurrentCamo,
        setCamo: setCamo,
        travelTo: travelTo
    };

    function openDoor() {
        doorOpen = true;
    }

    function closeDoor() {
        doorOpen = false;
    }

    function travelTo(destination) {
        // TODO(ads): implement this once we figure out
        // the bit about time-travelling.
    }

    function getCurrentCamo() {
        return currentCamouflage;
    }

    function setCamo(newCamo) {
        throw new Error('I won\'t do that, and you know it…');
    }
}
```

If you run `git log`, you'll see that the last commit is called "feat(tardis): add methods for door and camouflage". You can run `git show HEAD` to show both the commit message and the changes made in the latest commit. You will see that the commit added methods concerning the door and the camouflage. Since we use what's called "atomic commits", we want to have one commit for the door related changes, and another one for the camouflage related changes.

---

Aside: "Atomic commits" are when each functional change is contained in a single commit, and each commit only contains one functional change. It's a little much to dive into right now, but we will come back to this in later exercises.

---

Run `git reset HEAD~1`.

We have now taken "a step back" in the history of this branch. The latest changes are still in the file, but they are no longer committed. Let's imagine that you just made these changes, and now want to commit them into two different commits.

Run `git status` to see which files have been changed, and `git diff` to see the changes in them.

With the `git add` command, we can stage all modified files at once (using `git add -A`), or only the files we specify (using `git add exercises/README.md` for example). But we can also add only *parts* of a file.

Run `git add -p` and add only the changes relating to the door. You will get a prompt where you can enter a choice for what to do. One of the options is `?`, which will give you an explanation of each option. Note that git will print this explanation, and then print the current diff section *after* it, meaning that you might have to scroll upwards to see the help that was just printed. By the way, it looks like we added a few unnecessary line breaks around the variables at the top of the `createTardis` function. Don't add those to either commit.

Now commit the staged changes with a relevant commit message.

Then add the camouflage related changes.

Now commit those changes.

To get rid of the changes we don't want to keep, run `git checkout .`. This checks out the last version of all files, and thus replaces the version with the extra line break with the version you just committed, that has no extra line break.

So, what if that change we just threw away wasn't just a blank line, but something important that we really ought to have kept?

Well, in our case, for one, that change is still available on GitHub, since we haven't pushed any of our changes to the remote repo. But it's available here on your local computer as well. It's just a bit hidden. We can go into the "reflog" and find the reference to it, and then check it out that way. So basically, it's a little bit of a hassle, but it's possible. Had we branched off to a new branch before doing the reset, it would have been even simpler, since we would just have to check out the old branch.

But, in this exercise, we imagined that we had actually made these changes right now, and they had never been committed to git before. What if that was actually the case? Well, then those changes would have really been gone. git never knew about them, so there's no way for git to restore them.

This is one of the reasons why you should commit early and often. Not after every keystroke of course, but every once in a while, and definitely not only after a whole week of work. Once something is in git, you can always get it back, and you can still go back and re-write the commit history if it's ugly.

Once you push the branch to the remote repository, your work will even be backed up on another computer. Once you start sharing a branch with a colleague though, you will want to make sure you are on the same page about changing the history of the branch, as it can sometimes be a bit of a bother if you both make different kinds of changes.

Either way, you'll want to not change the history of the `main` branch, as that's the most important branch in the repo, and you really want to minimise the risk of any headaches there.

With public repos on GitHub, it's considered bad form to change history, since any number of other people might have made copies of your repo. (That's a rule I'm breaking in this repo by the way, but only because the git history is actually part of the course material in this case.)

Some people say that you must never *ever* change history in a branch you've pushed to a remote repo, but really, it's fine as long as everybody working on the repo is aware and on the same page about these things.

*If you're unsure, ask your teammates!*

Now go take a look at the exercises for "squashing".
