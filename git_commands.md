##create a git new repository on the command line

echo "# dvc-poc" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:sasthana-paxcom/dvc-poc.git
git push -u origin main

