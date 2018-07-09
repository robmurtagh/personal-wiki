
* Amend the last commit:

```bash
git commit --amend
git commit —-amend —-no-edit
```


* Squash commits:

```bash
git rebase --interactive --root
```


* Force squash commits - e.g. down to root commit:

```bash
rm -rf .git
git init
git add .
git commit -m "Initial commit"
```


* Forget file after adding to .gitignore
```bash
git rm --cached CREDENTIALS.py
```

* Push tags to origin:
```bash
git push origin --tags
```


* General force push

```bash
git push -—force origin
```


* Git equivalent of SVN update - something along the lines of... :

```bash
git stash
git pull
git stash pop
```