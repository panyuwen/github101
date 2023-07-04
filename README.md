#### 1. Git global setup
```bash
## Both user name and email address are required
git config --global user.name "your.user.name"
git config --global user.email "your.email.address"
```

#### 2. Create a new repository
```bash
## Download the demo, you can create a new repository later
git clone https://github.com/panyuwen/github101.git
	
## Working directory
cd github101

## Create a new working file, or modify an existing file
touch README.md

## Add file contents to the index
git add README.md

## Record changes to the repository
git commit -m "README"

## Update remote refs along with associated objects
git push -u origin master
```

If the "push" step FAILS, run step 3 to update your current repository. Then "add, commit, and push", again.

#### 3. Update your current working files
```bash
## Fetch from and integrate with another repository or a local branch. You'd better know the difference between "pull" and "fetch"
git pull origin master
```

#### 4. Existing folder
```bash
## create a repository on github, but without README file
cd existing_folder
git init
git remote add origin https://github.com/panyuwen/existing_folder.git
git add XXX
git commit -m "Initial commit"
git push -u origin master
```

#### 5. Existing Git repository
```bash
cd existing_repo
git remote add origin https://github.com/panyuwen/existing_repo.git
git push -u origin --all
git push -u origin --tags
```

#### 6. Modify the commited user name & user email if you want
```bash
# user name & email
git config user.name 'Yuwen Pan'
git config user.email 'panyuwen.x@gmail.com'
```

write the following code into the script named email.sh, and change the parameters "OLD_EMAIL", "CORRECT_NAME", "CORRECT_EMAIL"    

```bash
#!/bin/sh

git filter-branch --env-filter '

OLD_EMAIL="some_old_email@something"
CORRECT_NAME="Yuwen Pan"
CORRECT_EMAIL="panyuwen.x@gmail.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

```bash
# run
chmod +x ./email.sh
./email.sh

# check
git log
```

```bash
# run the following code if failed executing the above steps
# then run ./email.sh again

git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch Rakefile' HEAD
```

```bash
# push & finish
git push origin --force --all
```

