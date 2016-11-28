
`git merge` joins two development histories together

```
a-b-c-d-e (master)
    |
    x-y-z (branch1)
```

If each letter above is a commit and you have two branches: (1) master and (2)
branch1 then you can squash and merge commits from branch1 into master using
this command:

```sh
$ git checkout master
$ git merge --squash branch1
$ git commit
```

This will take all your commits from the `branch1` branch and squash them
into one commit and merge them into master. This is the scenario in which there
are no conflicts.
