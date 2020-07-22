# Class Learnings - FbW39

Here will be listed what we've done and learned during the classes of FbW39.


## 22.07.20

- ### Differences between local and remote repositories

We learned the difference between **local** and **remote** repositories. We learned how they interact with each other with the opposite commands ***`git push`*** and ***`git pull`*** .

> - The **local repository** is the one located in your computer. Changes done locally are committed to it.
> - The **remote repository** is the one that is located remotely, in our case hosted in GitHub. Our local changes are not visible there until they are pushed to it.
> - ***`git push`*** is the command line that pushes the changed committed in our local repository into the remote repository, making it available to the other developers.
> - ***`git pull`*** is the command line that pulls the changes available in the remote repository into our local repository, so we can use the work done by other developers.
> - An empty folder **cannot be pushed** to the remote repository.

- ### Changing Branches

We learned how to switch between our available branches with the ***`git checkout`*** command, and that a change done in one branch is not applied to others. We also learned how to list the available branches with the ***`git branch`*** command.

> - To see all the branches available in the remote repository, use ***`git branch -r`*** instead.
> - To change to a non-existent branch, use ***`git checkout -b [BRANCH_NAME]`*** instead. the **-b** flag creates a new branch.

- ### Merging Branches

We also learned how to merge a branch into another with the ***`git merge`*** command, which basically pulls all the commits done on the specified branch into your local branch.

> - The merge command is specified as ***`git merge [TARGET_BRANCH]`*** and should be executed within the branch you want to bring the changes into.

- ### Creating a new repository from the terminal

We learned how to create a new repository directly with the command line, use the public GitHub API.
> - ***`curl -u '[USER]' https://api.github.com/user/repos -d '{"name":"[REPO]", "private":false}'`*** is the command line to do so, providing to the API your username and the repository's name.
> - For more information about the *Public GitHub API* check the official [GitHub REST API Documentation](https://docs.github.com/en/rest).
