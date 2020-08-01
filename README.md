#### 1. ***Git global setup***
	## Both user name and email address are required
	$ git config --global user.name "your.user.name"
	$ git config --global user.email "your.email.address"

#### 2. ***Create a new repository***
	## Download the demo, you can create a new repository later
	$ git clone https://github.com/panyuwen/learn_github.git
	
	## Working directory
	$ cd learn_github
	
	## Create a new working file, or modify an existing file
	$ touch README.md

	## Add file contents to the index
	$ git add README.md
	
	## Record changes to the repository
	$ git commit -m "README"
	
	## Update remote refs along with associated objects
	$ git push -u origin master
	
`If the "push" step FAILS, run step 3 to update your current repository. Then "add, commit, and push", again.`

#### 3. ***Update your current working files***
	## Fetch from and integrate with another repository or a local branch. You'd better know the difference between "pull" and "fetch"
	$ git pull origin master

#### 4. ***Existing folder***
	$ cd existing_folder
	$ git init
	$ git remote add origin https://github.com/panyuwen/existing_folder.git
	$ git add .
	$ git commit -m "Initial commit"
	$ git push -u origin master

#### 5. ***Existing Git repository***
	$ cd existing_repo
	$ git remote add origin https://github.com/panyuwen/existing_repo.git
	$ git push -u origin --all
	$ git push -u origin --tags

