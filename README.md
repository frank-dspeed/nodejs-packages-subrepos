# nodejs-packages-subrepos
I need to clean up my github Account a bit so i Create this Repo with so called git subrepo to preserve the historys

This Repo holds 2 subrepo types subrepo and dirrepo the later is a own created name for that repo type it is simply the original preserved git history rewritten via a little shell script that runs some git commmands. The subrepo Repos are referencing projects that are under more heavy development.

So This is a Less Active Maintained Public Archiv of some stuff mostly for my own memorys.

## subrepo
https://github.com/stealify/git-subrepo
```
git subrepo clone <remote-url> [<subdir>]
git subrepo init <subdir>
```


## SubDir Repo
https://github.com/frank-dspeed/nodejs-packages-subrepos
```
./subdir.sh <subdir> <remote-url> <branch>
```
