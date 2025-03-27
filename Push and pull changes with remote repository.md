Push and pull changes with remote repository

Create a new repository on the command line:
echo "Some text you want to add in README.md file" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin repository_link
git push -u origin main

Pushing existing repository from the command line:
git remote add origin repository_link
git branch -M main
git push -u origin main <- the u option is used to set upstream
