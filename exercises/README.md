Good stuff! You found the first exercise!

And in so doing, you also completed the first task in the first exercise. Isn't
this going just swell?

Branches makes it possible to keep different versions of your repository, and
switch easily between them. All repositories have a branch called `master`.
Unless your project is fairly complex, and deals with multiple release-tracks,
`master` is the branch you will probably be building your releases from.

All development however, should be done on separate branches. When you start
a new task of some sort, a bugfix, a new feature, cleaning up some old code,
etcetera, you start by creating a new branch.

When you create a new branch, the current state of the branch you where on is
kept as the starting point for the new branch.

Usually, you will start a new branch from `master`, but you can branch off from
any existing branch. Know what? Why don't you go ahead, and make a new branch
off of this one?

Done? Great. As you can see, nothing at all has changed. (Except that if you run
`git status`, you will see that you are now on the new branch.)

But any changes on this new branch are isolated from the old branch that you
started out on. Try it out! Make some changes in this file, add some text or
something. Then run `git add -A` to tell git that this change should be
saved. This is called "staging" the changes. "Saving" those changes is called
"committing" them, and that's what we'll do next.

Run `git commit -m "My first commit"`.

Now, all this "staging" and "committing" might seem like a lot of jumping
through hoops. In the beginning, "staging" is mostly something you forget to do,
and then git becomes all annoying and prissy when you try to do an empty commit.

But, there is good reason for staging and committing as separate steps, and
we'll come to that :)

Now run `git log -3`. This should show you a list of three commits, where the
first commit shown is yours, and the next two are the last commits I did on the
branch `exercises/branches`. See how history is preserved from the old branch?

Now checkout `exercises/branches` again. Notice how this file changed back to
the way it looked before your changes? You can still find your changes if you
check out your branch again. Do it if you're paranoid, but come back here
afterward!

Now we'll do some house cleaning and delete your version of the branch. Deleting
a branch is also done through the `git branch` command. If you don't know how,
run `git branch -h` to get some condensed help for the command. If you run
`git branch --help` instead, you should get a webpage with a little more
explanation of each command. This way you can get technically correct
information about pretty much every command in git. It's a good place to start,
but if you find it about as easy to digest as a harboiled rock, no one will
blame you for googling… :)

Ok. So what if instead of throwing all your work away, you want to keep it?

Go ahead and create a new branch from this one.

Now fiks my bad speling.

Leave this sentence where it is.

But delete this one.

Then run `git diff` to show the changes you made. Nifty, isn't it? Stage and
commit your changes with a nice commit message. Then checkout
`exercises/branches` again.

Now merge your branch into this branch. If you did it correctly, you should see
your commit when you run `git log`. You will also see that this file has
now been updated with your changes.

Now might be a good time to look at the excercises for commit.
