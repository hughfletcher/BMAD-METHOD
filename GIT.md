# When v5.1.4 arrives

```bash
# create a new release branch at the new upstream tag
git fetch upstream --tags
git switch -c rel/v5.1.4 tags/v5.1.4
git push -u origin rel/v5.1.4

# rebase your long-lived feature branch onto the new tag
git switch custom-v5
git rebase rel/v5.1.4        # resolve conflicts once per release, if any
git push -f origin custom-v5  # rebase => force push

# fast-forward the release branch to include your updated changes
git switch rel/v5.1.4
git merge --ff-only custom-v5
git push
```