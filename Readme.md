## Readme.md

### To ignore larger files:
1. Get all files greater than 50MB
```
Get-ChildItem -Recurse $pwd | where Length -gt 50MB
```
2. Add those files name to .gitignore
3. Continue as usual
```
git add ...
git commit -m "Some description"
git push origin master
```


### To track larger files:

1. Install "Git Large File Storage" from https://git-lfs.com/
2. Execute
```
git lfs install
git lfs track "*.pdf"
git lfs track "*.zip"
git lfs track "*.csv"
git add .gitattributes
```
3. And then continue as usual
```
git add ...
git commit -m "Some description"
git push origin master
```

To restore previous commit:
```
git reset --soft HEAD~1
git restore --staged .
```

If you have already commited and then add something to the .gitignore, you can execute to start again
```
git rm -rf --cached .
git add .
```


#### Documentation
- [.gitignore file generator](https://mrkandreev.name/snippets/gitignore-generator/)
- [Python Git Ignore Template File](https://github.com/github/gitignore/blob/main/Python.gitignore)
- [Git Large Files - glf](https://git-lfs.com/)
- [How To Upload Large Files to GitHub Repository](https://medium.com/linkit-intecs/how-to-upload-large-files-to-github-repository-2b1e03723d2)
