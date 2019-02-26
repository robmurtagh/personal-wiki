# Git

## Amend the last commit

```bash
git commit --amend
git commit —-amend —-no-edit
```

## Squash commits

```bash
git rebase --interactive --root
```

## Force squash commits - e.g. down to root commit

```bash
rm -rf .git
git init
git add .
git commit -m "Initial commit"
```

## Forget file after adding to .gitignore

```bash
git rm --cached CREDENTIALS.py
```

## Push tags to origin

```bash
git push origin --tags
```

## General force push

```bash
git push -—force origin
```

## 'SVN update'

Something along the lines of should bring underlying versions up to date:

```bash
git stash
git pull
git stash pop
```

## Show remote URL

```bash
git remote show origin
```

## Useful resources

- [Using master, release and feature branches](https://medium.freecodecamp.org/how-to-use-git-efficiently-54320a236369) as a team

## Download one folder from repo

Use [DownGit](https://minhaskamal.github.io/DownGit/#/home)