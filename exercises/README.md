Ok. So we've split a single commit into a few smaller commits.

What if we want to combine commits instead?

If you run `git log` on this branch, you'll see that I've been quite busy with committing when writing this exercise. I think you'll agree I've gone a bit far…

There's quite a handy tool for fixing this though. It's called "interactive rebase". Since "interactive rebase" is a bit of a mouthful, and "squash" is the action you'll probably most often use it for, I'll often use the term "squashing" for the whole process of performing an interactive rebase. (Well, OK, you'll probably actually mostly use the "fixup" action, but that's basically the same as "squash" and "fixuping" sounds beyond stupid 🙈)

To run an interactive rebase, run `git rebase -i <starting point>`.

As you can see, you need to supply a starting point. This starting point is the last commit you *don't* want to include. This might seem counter-intuitive, but remember that we are performing a *rebase*. We take everything after the given commit, change it to our liking, and "rebase" it onto the given commit.

Run `git log` and find the commit called "feat(exercises): add exercise on squashing commits". Then copy the hash of the commit just *before* that (i.e. the first *older* commit).

Now run `git rebase -i <hash>`.
