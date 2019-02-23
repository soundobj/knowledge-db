- [Rebase vs Merge](#rebase-merge)
- [Gitflow](#gitflow)

## Rebase vs Merge <a name="rebase-merge"></a>
git merge apply all unique commits from branch A into branch B in one commit with final result<br />
- git merge doesn’t rewrite commit history, just adds one new commit<br />
- git rebase gets all unique commits from both branches and applies them one by one<br />
- git rebase rewrites commit history but doesn’t create extra commit for merging<br />

## gitflow <a name="gitflow"></a>
One of the great things about GitFlow is that it makes parallel development very easy, by isolating new development from finished work. New development (such as features and non-emergency bug fixes) is done in feature branches, and is only merged back into main body of code when the developer(s) is happy that the code is ready for release.<br />
Although interruptions are a BadThing(tm), if you are asked to switch from one task to another, all you need to do is commit your changes and then create a new feature branch for your new task. When that task is done, just checkout your original feature branch and you can continue where you left off.<br />
- New development (new features, non-emergency bug fixes) are built in feature branches:<br />
- Feature branches are branched off of the develop branch, and finished features and fixes are merged back into the develop branch when they’re ready for release:<br />
- When it is time to make a release, a release branch is created off of develop:<br />
- The code in the release branch is deployed onto a suitable test environment, tested, and any problems are fixed directly in the release branch. This deploy -> test -> fix -> redeploy -> retest cycle continues until you’re happy that the release is good enough to release to customers.<br />
- When the release is finished, the release branch is merged into master and into develop too, to make sure that any changes made in the release branch aren’t accidentally lost by new development.<br />
- The master branch tracks released code only. The only commits to master are merges from release branches and hotfix branches.<br />
- Hotfix branches are used to create emergency fixes:<br />
