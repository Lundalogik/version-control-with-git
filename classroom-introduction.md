# Classroom introduction

New users are often afraid of git. I believe the reason is that they are not comfortable in their understanding of how git works.

I hope to cure you of such fears, if you have them.

git is very powerful, and therefore often assumed to be very complex. But the core of git is actually incredibly simple. Once you understand how the core works, it demystifies all the complex functionality built on top of that core.

At its core, git is basically two things (simplified, not necessarily 100 % *technically* correct, but it's what you need to know):

1. A veritable shitload of copies of all your files in every state you ever committed. (We call these "commits".)
    * These commits are *never changed*. The only change is that new commits are *added*. (Each copy has its own unique hash, which also will *never change*.)
1. A structure of references to those commits.
    * These references can be changed, added, deleted, etcetera.

This is important, because it has some fundamental effects. Most important is the fact that the only way any git command *ever* operates on the first part, the commits, is by *creating new* commits. Every time a command appears to change, move, or delete anything, it operates on the *second* part, the structure of references (or both parts, but still, only ever by *adding* new commits).

To really gain an understanding of this concept, it's almost time we start doing some exercises, actually performing these operations and seeing their effects.

But first, one *really small* bit of advanced git:

Any operation you perform is logged by git. So even if you remove a reference to a commit from the structure of references, your running of that command, *complete with a reference to the commit*, is stored in git's log.

This means that while you may accidentally "hide" a commit by deleting the reference to it, it's pretty hard to actually get rid of *every* reference to it, and it's not something you will happen to do by accident. So don't worry :)

On to the exercises!
