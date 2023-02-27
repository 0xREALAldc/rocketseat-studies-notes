`Open editor inside the REPOSITORY` 
-  If you type `.` with a repository open in github on your browser, it'll open for you a editor where you can edit, add new files and commit them to the repo

`Branches` 
-  *branches* are ramifications in our repository, that are separated from the *main work* and can be merged together after
-  *git branch* use this command in your terminal to list all the branches that exist and a `*` will be shown beside the one that you're in
-  *git checkout -b [name for the branch]* the *-b* is used when we want to *CREATE A NEW* branch
	-  EG: `git checkout -b BranchTest` 

`Merge` 
- is when we get a side branch and put all the changes that we're done in that branch on our *main* 
- we need to go to the branch that we want to put the *fresh changes* in 
	- then we will use the command `git merge [name of the branch]`
	- this command will get all the commits from the *secondary* branch and puts inside the *main* branch that you choose

`Erase a branch`
- `git branch -D [name of the branch to be deleted]` this command will erase the branch that we choose. This will erase *ONLY* in your local machine, the branch will still exist in your repository
	- after we need to push the modification to our repository with the command `git push origin main` 
`git push origin --delete [name of the branch to be deleted]` this command will erase the branch in the repository, not only in your local machine

`Refreshing the local branches` 
- `git branch -a` this command shows you all the branches that exist in your local machine, and also the ones that only exists in your repository but you don't have a clone in your local machine
- `git fetch` will refresh your local branches to match the ones from your repository
- `git fetch -p` will refresh your local branches to mach the ones from your repository, *REMOVING* the ones that we're delete remotely
	- this command will only update locally the *list* that your local machine have of the branches that exists in the repository, but if you have done a *git checkout* one time to a branch that was deleted, you will need to use the command to delete locally

`Configuration for the default branch`
- we need to open the repository in the browser 
	- go in *Settings*
	- go in *Branches*
	- then go in *Branch protection rules* 
	- then we can add some of the rules that are listed in there, like *request a pull request before merging*...

`Pull request (PR)`
- is a request to send some commit changes from one branch to another
- *LGTM* looks good to me, it's a very used commentary for PR's to when we *approve* a PR and don't have any comments to make anymore
- `Creating a PR`
	- we open our repository in the browser
	- go to *Pull requests* 
	- go to *New pull request*
	- now we have to set up some things
		- *base* will be always the branch that you want to *RECEIVE* the changes 
		- *compare* the branch that will be merged with the *base* branch
			- if we have any conflicts, it'll make us resolve first and then push the changes
		- then click in the *Create pull request*
		- when we *make* and *push* changes to a PR we have to request the reviewers to review again the PR
- `Open a PR on other people's projects`
	- we can add a PR to other persons projects even if we are not a project member, all we need is
		- fork the project
		- do the changes that we think are needed 
		- commit to the forked repo that is in our github
		- and then in the page of the repository will show a message like *This brnach is X commits ahead of [name of the original repository]* and will have a button with the name *Contribute* in the right, where if we click on will show a button *Open pull request* 
		- we also can go to the repository page that we want to open a pull request, click in *pull request* and click in *new pull request*, and then to compare to *YOUR FORK* you click in the link that says *compare across forks* to select our forked repository 

`Issues` 
- things that are pending to solve, like a bug or a new feature to develop
- we can open one that will be linked to a PR later

`Projects in github`
- we have a tab called *Projects* in github, that will give a option to create a project with *kanban boards* or *list the issues* 
- we can use *ONE PROJECT* for more than one *repository*, like if you have a project that have the *frontend, backend and mobile* being built in different repositories, we can centralize the issues and tasks in one project linking to the three repos
- let's say that we choose the *kanban style* 
	- we can set tasks in the *TODO* board, that after we can *convert to issue* 
- after we create a project, we can go to our *repository* and link the project in the repository
	- after you're inside the repository page, open the *Projects* tab and click on *Add project* and just select the project that you desire
