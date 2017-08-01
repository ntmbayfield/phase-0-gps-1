###**Merging & Pull Requests in GitHub**

**Merging in GitHub**
You can create a new feature branch and navigate to it by using the following command:
```
git checkout -b <new_feature_branch_name>
```

Once on the new branch, you would utilize the following commands, to go thru the process of making a new commit of any changes you've been working on:
```git status```.
```git add <file_name>```.
```git commit -m <commit message>.
```

You would then want to push any commits you've made on your local repository back up to GitHub,
by entering:
```git push <remote> <branch>```

Once you push a new branch up to your repository, GitHub should prompt you to create a pull request.  But if it fails to do so, you will need to open a pull request from the new branch to the original
repo.

**Pull Requests In GitHub**.

*What is a pull request?*.
Pull requests let you tell others about changes you've pushed to a repository on GitHub. Pull requests can only be opened if there are differences between your branch and the upstream branch. You can specify which branch you'd like to merge your changes into when you create your pull request.

*How do you create and merge a pull request?*
You create a pull request by navigating to the main page of the repository on Github.  In the “Branch” menu, choose the branch that contains your commits.  To the right of the Branch menu, click New Pull Request.  Use the base branch dropdown menu to select the branch you'd like to merge your changes into, then use the compare branch drop-down menu to choose the topic branch you made your changes in.  Type a title and description for your pull request.  Click Create pull request.

Once you’ve created a pull request, to merge it you want to start by navigating to the page for your repository and then clicking Pull requests.  In the "Pull Requests" list, click the pull request you'd like to merge.  Depending on the merge options enabled for your repository, you can:
  -Merge all of the commits into the base branch by clicking Merge pull request. If the Merge pull request option is not shown, then click the merge drop down menu and select Create a merge commit.
  -Squash the commits into one commit by clicking the merge drop down menu, selecting Squash and merge and then clicking the Squash and merge button.
  -Rebase the commits individually onto the base branch by clicking the merge drop down menu, selecting Rebase and merge and then clicking the Rebase and merge button.

For more information on merging and pull requests, [click here] (https://www.atlassian.com/git/tutorials/comparing-workflows).


