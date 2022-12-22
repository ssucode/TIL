# Git Config
### Config 종류 (우선순위순)
1. .git/config
2. ~/.gitconfig 혹은 ~/.config/git/config
3. /etc/gitconfig

### 명령어
사용자의 이름과 이메일을 설정하는 명령어
```Shell
git config user.name "<user_name>"                   # .git/config에 저장됨
git config user.email "<user_email>"                 # .git/config에 저장됨

git config --local user.name "<user_name>"           # .git/config에 저장됨
git config --local user.email "<user_email>"         # .git/config에 저장됨

git config --global user.name "<user_name>"          # ~/.gitconfig에 저장됨
git config --global user.email "<user_email>"        # ~/.gitconfig에 저장됨

sudo git config --system user.name "<user_name>"     # /etc/gitconfig에 저장됨
sudo git config --system user.email "<user_email>"   # /etc/gitconfig에 저장됨
```

 모든 설정값을 읽는 명령어
 ```Shell
 git config --list
 ```
 
특정 설정값을 읽는 명령어
 ```Shell
git config "<key>"
git config --show-origin "<key>"
 ```
 
  main 이라는 이름을 기본 브랜치명으로 사용하는 명령어
 ```Shell
 git config --global init.defaultBranch main
 ```
  
