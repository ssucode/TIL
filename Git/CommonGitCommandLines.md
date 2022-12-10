Common git command lines
Just taking a break from my little series, today I gather all popular and essential git command lines for myself (and you too if you’re interested!).
1. Power of the trinity
What trinity, you may ask? For me, it is
```
git add : add your work/ changes to a staging area; before committing them.
git commit -m “message”: add a message for your changes. Usually, it’s a brief of your changes.
git push: commit your work. It could be for a branch or the whole remote repository with local commits.
```
That’s it! Knowing the above 3 and you could do a basic git workflow!
2. Unstaged the file — git reset
```
git reset [file]: unstage the file, but preserve all of the content.
git reset [commit]: Remove all of the commits after the specified commit but still preserves those commits locally
git reset –hard [commit]: discards all commits histories and returns to the specified commit.
```
3. Make a new branch and merge or delete
```
git branch : list of current branches in the local repository.
git branch [branch name] : make a new branch
git branch -d [branch name] : delete the current branch.
git checkout [branch name]: switch to the specified branch
git checkout -b [branch name]: create a new branch and switch to that branch.
git merge [branch name]: merge the branch to another. (could be another branch or remote repository)
```
4. Clone a repository or update your current local repository
```
git pull [Repository Link]: fetches and merges changes to your local working repository from the remote server.
git clone [Repository Link]: clone an existing repository to your laptop/ computer from the remote server.
```
