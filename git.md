# GIT HELP 

## **Rules**

1. No commits/pushes to master :interdit:
2. Every feature (or every fix, anything new from master) is a new branch. Never work in a master branch!
3. Never re-use branches

## **Recommendations**

1. Commit often (every time you’re happy/your code working). Remember, commits are “saves” or “snapshots” of your local code, something for you to rollback to if something breaks and also to track your own progress!
2. Don’t underestimate the power of PR interface on Github. Describe your changes, read code, ask questions, ask for corrections before you merge!

## **GIT CHECKLIST **
 
**Ideal case: (done with feature) You finished working on the feature/branch, and there were no changes to remote master while you worked on it (or you don’t care about them)**

1. :terminal:  `gst` # is it green/red? if green — 2.
2. :terminal:  `git add . && git commit -m "describe change in present tense` # e.g.: “change button position”
3. :terminal:  `git push origin name-of-your-branch`
4. :github: `hub browse` to go to the GitHub web interface
5. :github: You will notice a prompt asking you to create a Pull Request, use the prompt
6. :github: Describe your changes and create Pull Request :danger: Don’t merge yourself unless 1000% sure
7. :github: Lead programmer closes your PR (merges your changes to remote master). But you’re not done yet!
8. :terminal: `git co maste`r # to get back to master
9. :terminal: `git pull origin master` # to update your local master with remote changes
10. :terminal: `git sweep` # to delete the branch you’re done with
11. :terminal:  `git co -b my-new-feature` # because life is hard and you never stop working

**More realistic case (still working on a feature, need new master) You HAVE NOT finished working, the remote master has been changed and you need these changes locally to continue working in a branch**

1. :terminal: `gst # is it green/red?` if green — 2.
2. :terminal:  `git add . && git commit -m "an explanatory description in present tense"`
3. :terminal: `git co master` # to change to local master
4. :terminal: `git pull origin master` to get the remote master with all latest changes
5. :terminal:  `git co your-current-branch-name` to switch back to your branch
6. :terminal: `git merge master` to merge remote changes to your current branch. A new editor window may appear, you can just close it (don’t leave it open or the merge won’t complete!)
:danger: :danger: :danger:

ACHTUNG! Conflicts!!!

7. Relax :soulagement:
8. :sublime: Resolve conflicts by going to all conflicted files and keeping just one good version of code (talk to other people here!). You may want to run rails `db:migrate` in your merging branch too (if you have a conflict in a schema).
9. :terminal: `git add . && git commit -m "resolve conflicts"`
**** IF YOU ARE DONE, DO 10 and 11, IF NOT CONTINUE WORKING ON YOUR FEATURE TILL DONE ***
10 :terminal: `git push origin your-current-branch-name`
11. :github: / :terminal: Follow steps 4-11 from the best case scenario
