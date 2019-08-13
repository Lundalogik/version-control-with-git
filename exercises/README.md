Good stuff! You found the first exercise!

And in so doing, you also completed the first task in the first exercise. Isn't this going just swell?

Branches make it possible to keep different versions of your repository, and switch easily between them. All repositories have a branch called `master`. Unless your project is fairly complex, and deals with multiple release-tracks, `master` is the branch you will probably be building your releases from.

All development however, should be done on separate branches. When you start a new task of some sort, a bugfix, a new feature, cleaning up some old code, etcetera, you start by creating a new branch.

When you create a new branch, the current state of the branch you where on is kept as the starting point for the new branch.

Usually, you will start a new branch from `master`, but you can branch off from any existing branch. Know what? Why don't you go ahead, and make a new branch off of this one?

Done? Great. As you can see, nothing at all has changed. (Except that if you run `git status`, you will see that you are now on the new branch.)

But any changes on this new branch are isolated from the old branch that you started out on. Try it out! Make some changes in this file, add some text or something. Then run `git add -A` to tell git that this change should be saved. This is called "staging" the changes. "Saving" those changes is called "committing" them, and that's what we'll do next.

Run `git commit -m "My first commit"`.

Now, all this "staging" and "committing" might seem like a lot of jumping through hoops. In the beginning, "staging" is mostly something you forget to do, and then git becomes all annoying and prissy when you try to do an empty commit.

But, there is good reason for staging and committing as separate steps, and we'll come to that :)

Now run `git log -3`. This should show you a list of three commits, where the first commit shown is yours, and the next two are the last commits I did on the branch `exercises/branches`. See how history is preserved from the old branch?

Now checkout `exercises/branches` again. Notice how this file changed back to the way it looked before your changes? You can still find your changes if you check out your branch again. Do it if you're feeling paranoid, but come back here afterward!

Now we'll do some house cleaning and delete your version of the branch. Deleting a branch is also done through the `git branch` command. If you don't know how, run `git branch -h` to get some condensed help for the command. If you run `git branch --help` instead, you should get a page with a little more explanation of each command, either in the terminal or as a webpage in your browser. This way you can get technically correct information about pretty much every command in git. It's a good place to start, but if you find it about as easy to digest as a harboiled rock, no one will blame you for googling… :)

Ok. So what if instead of throwing all your work away, you want to keep it?

Go ahead and create a new branch from this one.

Now fiks my bad speling.

Leave this sentence where it is.

But delete this one.

Then run `git diff` to show the changes you made. Nifty, isn't it? Stage and commit your changes with a nice commit message. Then checkout `exercises/branches` again.

Now merge your branch into this branch. If you did it correctly, you should see your commit when you run `git log`. You will also see that this file has now been updated with your changes.

---

A note on merging and rebasing (feel free to come back and read this at a later time if it feels too complicated right now):

When merging two branches, the resulting history will have the commits ordered by the date and time they where originally created. While this might sound very reasonable, in practise it often doesn't create a very nice history. This is because when we use branches to add a feature, the commits in a branch usually belongs together, and even if they are nicely "sectioned" so that each commit contains a single complete change, the commits are often better understood when seen together.

When rebasing one branch "onto" another, the final history will have all the commits from the other branch first, and then all the commits from the branch you are currently on last. In practise, it's like if you had waited to create your branch until after all the new commits had already been added to the other branch.

In the Lime CRM Feature Team, we always use rebase when updating a branch with new commits that has been added to the "source" branch. For example, let's say I create a branch from `master`. I then add a couple of commits to my new branch. While I'm working, a new feature is added to `master`. If I want to update my branch with the new commits from `master`, I rebase *my* branch *onto* master. I do this by first making sure my local master is up to date, then I checkout my branch, and run `git rebase master`.

When adding the changes from a branch into `master`, we use GitHub's "Rebase and merge" function. It rebases the branch onto master, and then merges it into master. That way, all the changes from the branch will be added after any existing changes on master.

Whether you use merge or rebase when updating your branch with changes from `master` (or any other "parent-branch"), is ultimately a matter of personal taste. However, if you share your working branch with anyone, it's important that you all use the same option. If one of you merges new changes from master, and someone else rebases onto master, your git history will be royally effed up. (The actual files on the system will be fine, but you'll have commits appearing multiple times at different places in the history and stuff like that. Just make sure to avoid it.)

---

Now might be a good time to look at the excercises for commit.
