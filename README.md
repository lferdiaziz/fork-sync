# Fork Sync

Github action to sync your Forks.
This action automatically creates and merges a pull request with the head defined by `ownwer`:`head` into the base defined by `base`. If you create a PR in the same repository you can omit the `owner` parameter.

# Example Workflow

```
name: Sync Fork

on:
  schedule:
  - cron: 0 2 * * 1-5

jobs:
  sync:

    runs-on: ubuntu-latest
    
    steps:
    - uses: TG908/fork-sync@v1.1.0
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        owner: llvm
        base: master
        head: master
```

# Options

|  name 	                                          |   description	                        |
|---	                                              |---	                                  |
|   owner (optional)	                              |   Owner of the forked repository	    |
|   github_token	                                  |   Token  to access the Github API	    |
|   head (optional, default = master)	              |   Head branch	                        |
|   base (optional, default = master)	              |   Base branch	                        |
|   merge_method (optional, default = rebase)       |   merge, rebase or squash            	|
|   pr_title (optional, default = Fork Sync)        |   Title of the created pull request	|
|   pr_message                                  	  |   Message of the created pull request	|
