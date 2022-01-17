Ok. So we've split a single commit into a few smaller commits.

What if we want to combine commits instead?

Well, let's start with the simplest example: You have some new changes that you want to add to the latest commit. This is called "amending" the commit.

A typical case where you might want to amend a commit is when you've had a commit reviewed by a teammate, and you've gotten some feedback. Instead of adding a commit called "Review fixes" or similar, you can just amend the original commit.

It seems I forgot to add your favourite poem here:

Perhaps you could help me out and fix that for me? If you don't have a favourite poem, just add a line from a song or a quote or something…

Before committing, run `git log -2`. We'll come back to the output later.

When you're done, run `git commit --amend` to replace the last commit with this new one, containing the changes of the old commit as well as your newly added changes.

Now, run `git log -2` again. As you can see, the commit history looks the same as before. But, take a closer look at the commit hash for the two commits. The second to last one will be the same as in the output from before you amended the last commit, but the hash for the amended commit is different from before.

In fact, you can still get to the old version of that commit using that hash. For example, you can run `git checkout <hash>` (replace `<hash>` with the real hash). You will then be in what's called a "headless state", because you're not on a branch. But that's easily fixable by running `git checkout -b name-of-new-branch`. As always, the new branch will get its initial state from the state you where in when creating it. But, this is an aside really. We'll come back to using hashes when we look at cherry-picking.

Now let's get back to combining already existing commits.

If you run `git log` on this branch, you'll see that I've been quite busy with committing when writing this exercise. I think you'll agree I've gone a bit far…

There's quite a handy tool for fixing this though. It's called "interactive rebase". Since "interactive rebase" is a bit of a mouthful, and "squash" is the action you'll probably most often use it for, I'll often use the term "squashing" for the whole process of performing an interactive rebase. (Well, OK, you'll probably actually mostly use the "fixup" action, but that's basically the same as "squash" and "fixuping" sounds beyond stupid 🙈)

To run an interactive rebase, run `git rebase -i <starting point>`.

As you can see, you need to supply a starting point. This starting point is the last commit you *don't* want to include. This might seem counter-intuitive, but remember that we are performing a *rebase*. We take everything after the given commit, change it to our liking, and "rebase" it onto the given commit.

Run `git log` and find the commit called "feat(exercises): add exercise on squashing commits". Then copy the hash of the commit just *before* that (i.e. the first *older* commit).

Now run `git rebase -i <hash>`.

You'll get a text file with all the commits listed in order, with the oldest one first. Below them is a comment explaining some of the commands you can use to squash, remove, or edit the different commits.

The commit that adds the section about amending is a large-ish one, and I think it can be reasonable to keep that as its own separate commit. But I suggest squashing all the other commits into the first one.

Now it's time to look at the exercise for "cherry-picking". See you there!
