# svca-inescapavel

svca-inescapavel

## Merge workflow for PR branches

Use the following commands to update and merge the reviewed branch into the target branch:

```bash
git remote add origin git@github.com:MatVerse-py/svca-inescapavel.git
# or: git remote set-url origin git@github.com:MatVerse-py/svca-inescapavel.git

git pull origin codex/update-readme-with-resolved-version
git checkout codex/update-readme-with-resolved-version
git merge codex/fix-issues-flagged-in-pr-#5-review
git push -u origin codex/update-readme-with-resolved-version
```

If you have no `origin` remote configured yet, add it first as shown above.
