## Git

Set the git credentail
```bash
git config --global url."https://liuyangc3:${GITHUB_TOKEN}@git.example.com".insteadOf "https://git.example.com"
```

Remove all git branchs except `master` or `main`
```bash
git branch | grep -v -e master -e main | xargs git branch -D
```

Rebase remote master to local
```bash
git pull --rebase origin master
```

Amend a previou commit without changing commit
```bash
git commit --no-edit --amend
```

List tags
```bash
git tag --sort=-creatordate

# list remote tag
git ls-remote --tags origin
```

Add tag
```bash
export tag=v0.0.1
git tag -a $tag -m "commit message" && git push origin $tag
```

Remove a tag
```bash
export tag=v0.0.1
# local
git tag --delete $tag

# remote
git push --delete origin $tag
# or push empty tag
git push origin :$tag
```

allow auto push to remote new branch
```bash
git config push.autoSetupRemote true
```

Set http credential cache
```bash
git config --global credential.helper "cache --timeout=86400" # 86400s=24h
```

## Jetbrain IDEs

short cut | explaintion
---|---
⌘(Command) + ⌥(Option) + A | git add
⌘(Command) + L | goto line
⌘(Command) + ⇧(Shift) + F | search text in dir
⌘(Command) + ⇧(Shift) + R | replace text in dir
X | a\|b



## Others

⚡ Rmove all `<none>` docker images
```bash
docker rmi $(docker images -a --digests=true | awk '$2 == "<none>" { print $4}')
```

Skip Spectral Scan 
```bash
export SKIP_PRE_PUSH=1
git push
```

# teleport

Get instance UUID
```bash
tsh ls --search=10.49.212.235 -f json | jq '.[0].metadata.name'

# or
tctl nodes ls | grep 10.49.212.235
```

Detele insatnce by UUID
```
tctl rm node/5370cc0f-fbae-4c47-9178-319e09b9b5f6
```
