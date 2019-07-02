# Git Sync

A GitHub Action for syncing between two independent repositories using **force push**. 


## Features
 * Sync branches between two Github repositories
 * Sync branches to/from a remote repository
 * Github action can be triggered on a timer or on push
 * To sync with current repository, please checkout [wei/github-sync](https://github.com/marketplace/actions/github-sync)


## Usage

### Github Actions
```
action "repo-sync" {
  uses = "wei/git-sync@master"
  args = "$SOURCE_REPO $SOURCE_BRANCH $DESTINATION_REPO $DESTINATION_BRANCH"
  env = {
    SOURCE_REPO = ""
    SOURCE_BRANCH = ""
    DESTINATION_REPO = ""
    DESTINATION_BRANCH = ""
  }
  secrets = ["SSH_PRIVATE_KEY"]
}
```
`SSH_PRIVATE_KEY` can be omitted if using authenticated HTTPS repo clone urls like `https://username:access_token@github.com/username/repository.git`.

### Docker
```
docker run --rm -e "SSH_PRIVATE_KEY=$(cat ~/.ssh/id_rsa)" $(docker build -q .) \
  $SOURCE_REPO $SOURCE_BRANCH $DESTINATION_REPO $DESTINATION_BRANCH
```

## Author
[Wei He](https://github.com/wei) _github@weispot.com_


## License
[MIT](https://wei.mit-license.org)
