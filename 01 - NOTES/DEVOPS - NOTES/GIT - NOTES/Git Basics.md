---
created: 2025-03-24T21:44
updated: 2025-03-25T23:44
tags:
  - devops
  - git
  - vcs
  - local
  - remote
  - repository
  - tracking
---
#### What is Git?

- Git is a distributed version control system that tracks versions of files.
- Version control means we can go back and work with a different version of our code base.
- Distributed means that it has a remote repository which is stored in a server and a local repository which is stored in a computer of every developer which is working on a project, so every developer has a full copy of the codebase.
#### Local and Remote Repositories

1. Local
	- The local repository is on your own machine so you have direct access to it.
	- Teammates can initialise their own repository on their computers.
	- They can simply pull the data from the remote one.
	- When they have made some changes they push these changes to the remote repo.
	- In order to sync the data between local and remote we can pull the data from the data from remote repo into local repo.
	- Local Repository Stages
		- Working Area
			- It is where we have all the active changes.
			- Git does not know what to do with them yet, it just knows that these files contain some updates.
			- Working area has two more areas within it.
				- Untracked Area
				- Modified Area
		- Staging Area
			- This is where we contain the new changes that will soon be committed.
		- Committed Area
			- It has all the files that are committed.
2. Remote
	- The remote repository is usually a centralised server and is entirely optional.
	- We can save the changes that we made locally on this remote server.
	- Remote can be used whenever you need a backup of your data in case your information has lost, or whenever you are working on a team.

#### Git Starter

- Use the `git init` to initialise any git project.
- Create a file within that folder called `example.txt`.
- Then add the files into or remove any file.
- Make use `git status` command to check whether the files are in staging area or not.
- While making use of the `git status` command we can see the below information.

```bash
On master branch
	No commits yet
	
	Untracked files
		example.txt
nothing added to commit but untracked files present
```

- Default branch is master branch.
- Storing changes in a local git repo is called committing, as we haven't committed the changes yet so it shows `No commits yet`.
- With every commit we save the current state of our repo and show the changes we made to it.
- `Untracked files` these are the files that the git knows of but however we haven't told git what to do with them.
- We haven't told it yet that we want to add it to our local repo, so they are still untracked.
- The file is right now in the `Working Area`.
- Before we can commit a file, we first have to put it in the `Staging Area`.
- We can put it in the `Staging Area` by using `git add --filename` or `git add .` commands.
- Where the `git add --filename` is used to move particular file into the staging area and `git add .` will add every file within that folder into the `Staging Area`.
- Now let's add the `example.txt` file into the staging area by using the command `git add example.txt`.
- After the we have added our file into the staging area we can again check the status of files using `git status` and now we can see the files that needs to be committed.

```bash
On master branch
	No commits yet
	
	Changes to be committed:
		(use "git rm --cached <file>..." to unstage)
			new file: example.txt
```

- Now let's commit our change, a commit records the change of a repository compared to its previous state.
- In this case we did not have previous commits, so the addition of the file `example.txt` is a change compared to its previous state.
- In order the commit the files that are currently in the staging area, we run the `git commit -m "message"`.
- `-m` is a flag for the message.
- A commit stores a copy of the file in its current state one or set of files that are committed within the `.git` folder.
- If make changes in the committed file, git creates another copy where it is a modified version of that file with new changes.
- It is the current version of the file, which is now in a modified state.
- If this was a mistake then we can restore the file from the previous commit, by running the `git restore <file>...` command.
- So when we do that the current version of the file is updated with the contents of the file from the previous commit.
- Since there are no changes between current and the previous commit now, our working tree is clean and no commits are required.
- So let's say we rather make changes in the file and commits it into the git.
- Then git creates a new commit and stores a new copy of the current version of the story in that commit.
- The previous version of commit and the current version of the commit lives in git's commit history forever, allowing us to go back in any previous date or commit and look at the story at that time.
#### Git Best Practices

- Make every commit atomic, meaning each commit should be to solve a single problem or implement a specific feature or improvement.
- Each commit should have single set of change, it doesn't mean a single file it could be multiple files, but it should be solving a single set of change.
- To follow atomic commit we can maintain a clean history for the project and one that make sense.
- Add proper message in the commits.

#### Git Ignores You

- Let's say in your folder you created some files but you do not want a file to be tracked or commit, stage the file in the git.
- We can make use of a git file called `.gitignore`.
- After creating the `.gitignore` we can add the file name which we do not want to track or commit inside the `.gitignore` file.

#### Git Log

- We can see the commits that were made in the project in the terminal.
- Using the command `git log`, we can see the information that we need to know about all the commits.
- Such as commit hash, author name, date of the commit and the commit message.
- We can also see the log in one line using `git log --oneline`.
- You can also see the files committed in the log using `git log --name-only`.
#### Git Branches
- By default the branch is the `main` or `master` branch.
- Let's say a new developer joins in to work.
- We don't the developers to directly make changes to the `master` branch.
- But instead give them a separate version, where they can change code and commit to it until their work is done.
- In the mean we can also work upon our own branch.
- Only after their entire work is done and tested, then we want the new code in the production.
- A branch is basically a pointer to the last commit.
- If you are working on a feature then you might call it `feature/<feature-name>`.
- And only after the changes has been made and it is tested then only we merge those changes into the `master` branch.
#### Branches Command

- To create a new branch use the below command.
- `git branch <branch-name>`
- To see all the branches and the branch we are on use the below command.
- `git branch`
- To switch to an existing branch use the below command.
- `git checkout <existing-branch-name>`
- To create a new branch and immediately switch to it use the below command.
- `git checkout -b <branch-name>`
- To delete a branch use the below command.
- `git branch -d <branch-name>`

#### What is HEAD?

- A HEAD is where you are right now in the git repo.
- The HEAD points to the last commit in the branch that you are currently on.
- When you switch branches the HEAD moves with you.

#### Merging

- We can merge a branch with a `git merge` command.
- To merge with any branch first we need to `checkout` to that particular branch, and then we can merge other branches onto it.
- Git can perform `fast-forward merge` and a `no fast-forward merge`.
- A `fast-forward merge` can happen when the current branch has no extra commits compared to the branch that we are merging.
- This type of merge does not create a commit, but rather merges to commits on the branch that we are merging, right into the current branch.

#### Remote World of Repositories
- Most commonly used remote repos are:
	- Github
	- Gitlab
	- Bitbucket
- Once we successfully intialize a repo on one of these platforms, we get access to something called a connection string.
- A connection string is an url from which we can let git know where the repository is located.
- We can add the repository into our local project with the `git remote add` command.
- We want to add the alias  `origin` at last like this `git remote add origin` to make sure that we always know which remote repo we're pushing to without memorising the entire  connection string. 
- In order to do so we need to `git remote add origin <connection string>`.
- We can list all our remote repos using the command `git remote -v`.
##### Pushing Data
- In order to keep our local and remote repo in sync, we have to push the data from our local repo to the remote repo.
