Question 1
Action taken for Remote Repository
Create a private remote repository
Add classmate as collaborator
Actions Taken on Local Repository
Create a local repository
mkdir git_assignment_HeroVired
cd it_assignment_HeroVired
git init
Rename master branch to main (optional)
git branch -m master main

Create readme file
touch readme.md

Configuring remote repository
git remote add origin https://github.com/abhijeetchavan9243/git_assignment_HeroVired.git
git push -u origin main
Create a new brach named dev and checkout to dev branch
git branch dev
git checkout dev
git status
Create python app file
touch CalculatorPlus.py
vim CalculatorPlus.py
# press i to enter INSERT mode
# Paste the code provided in the problem statement 1 (command + v)
# Press esc to exit INSERT mode and click shift + :
# Type wq to save and exit then hit enter.
Stage and commit above changes to dev branch
git add CalculatorPlus.py
git commit -m "Add CalculatorPlus app to dev branch"
git push origin dev
Merge dev into main and release version 1
git checkout main
git status
git merge dev -m "Merge dev into main for v1.0 release"
git log --oneline
git push origin main
Release version 1 of CalculatorPlus app
git tag -a v1.0 5d8e0d3 -m "Release version 1.0"
git push origin v1.0
Create feature/sqrt branch and modify the changes
git checkout dev
git status
git branch feature/sqrt
git checkout feature/sqrt
git status
Modify the pythong file to implement sqrt feature
vim CalculatorPlus.py
# press i to enter INSERT mode
# Uncomment the sqrt function definition and funtion call.
# Press esc to exit INSERT mode and click shift + :
# Type wq to save and exit then hit enter.
Stashing work done in sqrt feature as need to fix bug in divide funtion on dev branch
git stash save "work in progress for sqrt feature"
git stash list
git checkout dev
git status
Modify the divide funtion to handle Division by Zero exception
vim CalculatorPlus.py
# press i to enter INSERT mode
# Modify the divide funtion to handle Division by Zero exception.
# Press esc to exit INSERT mode and click shift + :
# Type wq to save and exit then hit enter.
Stage, commit and push the bug fix changes
git add CalculatorPlus.py
git commit -m "Fix bug in divide function on dev branch"
git push origin dev
git status
Make sure both main and dev branches are up-to-date with origin
Install GitHub CLI to create PR from terminal
brew install gh
gh --version
gh auth login # Select GitHub.com and HTTPS
gh pr create --base main --head dev --title "Bug fix divide function merge dev into main" --body "Implemented bug fix in divide function on dev branch requested Munish to review the code and provide approval to merge dev branch with main" --reviewer munisekar-py
After PR is approved, and origin/dev is merged with origin/main, need to fetch this changes to local repo
git pull origin main
git checkout main
git status
git merge dev
git push origin main
As everything is up-to-date, lets start working on feature/sqrt
git checkout feature/sqrt
git status
git stash apply stash@{0}
git add .
git commit -m "Add sqrt feature"
git push origin feature/sqrt
Creating PR for merge of feature/sqrt with dev branch
git checkout dev
git status
gh pr create --base dev --head feature/sqrt --title "Implement sqrt feature and merge feature/sqrt into dev" --body "Implemented sqrt feature requesting Munish to review and approve it so that feature/sqrt branch can be merged into dev" --reviewer munisekar-py
Merging dev with main and publishing release version 2.0
git tag -a v2.0 -m "Release version 2.0"
git push origin v2.0
gh release create v2.0 --title "Version 2.0 Release" --notes "Added square root feature, fixed divide by zero bug and tested functionality of the app."
Question 2
Installing git lfs
brew install git-lfs
git lfs version
Creating a new branch named lfs
git branch lfs
git checkout lfs
git status
To uncommit recent commit
git reset --soft HEAD~1

Asking git lfs to track a big file
git lfs install
git lfs track "products-2000000.csv"
# After this command .gitattributes file will be created
# Add and commit these files
git add .gitattributes products-2000000.csv
git commit -m "Track and add products-2000000.csv with git lfs"
git push origin lfs
Question 3
Create new branch geometry-calculator
git checkout main
git status
git branch geometry-calculator
git checkout geometry-calculator
git status
Creating GeometryCalculator python file
touch GeometryCalculator.py
vim GeometryCalculator.py
# press i to enter INSERT mode
# Paste the code provided in question three of Git assignment.
# Press esc to exit INSERT mode and click shift + :
# Type wq to save and exit then hit enter.
Make sure geometry-calculator branch is up-to-date with origin before starting with workflow
git add .
git commit -m "Add GeometryCalulator app"
git push origin geometry-calculator
Create feature/circle-area branch and stash changes
git checkout geometry-calculator
git status
git branch feature/circle-area
git status
#Make changes to implement feature/circle-area
#Stash changes
git stash save "work in progress for feature/circle-area"
git stash list
Create feature/rectangle-area branch and stash changes
git checkout geometry-calculator
git status
git branch feature/rectangle-area
git status
#Make changes to implement feature/rectangle-area
#Stash changes
git stash save "work in progress for feature/rectangle-area"
git stash list
Now go back feature/circle-area branch and revert stashed changes and commit and push them
git checkout feature/circle-area
git status
git stash apply stash@{1}
git add .
git commit -m "Add feature/circle-area"
git push origin feature/circle-area
Now go back feature/rectangle-area branch and revert stashed changes and commit and push them
git checkout feature/rectangle-area
git status
git stash apply stash@{0}
git add .
git commit -m "Add feature/rectangle-area"
git push origin feature/rectangle-area
Create a PR to merge feature/circle-area into geometry-calculator
Once PR is reviewed and approved, merge feature/circle-area into geometry-calculator and pull changes to local repository
gh pr create --base geometry-calculator --head feature/circle-area --title "Add feature/circle-area to geometry calculator" --body "Implemented feature/circle-area to geometry calculator and requested Munish to reveiw and approve the merge" --reviewer munisekar-py
git checkout geometry-calculator
git status
git pull origin geometry-calculator
git merge feature/circle-area
git push origin geometry-calculator
Create a PR to merge feature/rectangle-area into geometry-calculator
Once PR is reviewed and approved, merge feature/rectangle-area into geometry-calculator and pull changes to local repository
gh pr create --base geometry-calculator --head feature/rectangle-area --title "Add feature/rectangle-area to geometry calculator" --body "Implemented feature/rectangle-area to geometry calculator and requested Munish to reveiw and approve the merge" --reviewer munisekar-py
git checkout geometry-calculator
git status
git pull origin geometry-calculator
git merge feature/rectangle-area
git push origin geometry-calculator
Create a PR to merge geometry-calculator into dev
Once PR is reviewed and approved, merge geometry-calculator into dev and pull changes to local repository
gh pr create --base dev --head geometry-calculator --title "Add geometry calculator to dev" --body "Implemented geometry calculator to dev and requested Munish to reveiw and approve the merge" --reviewer munisekar-py
git checkout dev
git status
git pull origin dev
git merge geometry-calculator
git push origin dev
Create a PR to merge dev into main
Once PR is reviewed and approved, merge dev into main and pull changes to local repository
gh pr create --base main --head dev --title "Add geometry calculator to main" --body "Implemented geometry calculator to main and requested Munish to reveiw and approve the merge" --reviewer munisekar-py
git checkout main
git status
git pull origin main
git merge dev
git push origin main
