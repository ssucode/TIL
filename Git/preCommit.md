# pre-commit
### pre-commit란?

* Commit시 문법 오류나 스타일, 정렬, 타입 오류 등을 미리 체크합니다.
* 개발자의 기호에 따라 선택하고 커스텀까지 할 수 있습니다.

### pre-commit 설치 - Python 예시
```Shell
git init
pip install pre-commit
pre-commit install
```
'.pre-commit-config.yaml' 파일을 생성
```
repos:
  - repo: https://github.com/ambv/black
    rev: ''
    hooks:
      - id: black
        language_version: python3.8 
  - repo: https://gitlab.com/pycqa/flake8
    rev: ''
    hooks:
      - id: flake8
  - repo: https://github.com/pycqa/isort
    rev: ''
    hooks:
      - id: isort
  - repo: https://github.com/necaris/pre-commit-pyright
    rev: ''
    hooks:
      - id: pyright
```

* black : 코드 포멧터, 코드 스타일을 통일시켜 줍니다.
* flake8 : 코드 린터, PEP8 규악을 지켰는지 검사합니다.
* isort : 파이썬 import를 정렬해주는 라이브러리입니다.
* pyright : 파이썬에서 타입을 체크해주는 라이브러리입니다. (mypy로 대체가능)

버전업데이트가 필요하면 아래 명령어를 먼저 실행한다.
```
pre-commit autoupdate
```
아래 명령어로 실행합니다.
```Shell
pre-commit run
```
Commit을 진행하여 정상적으로  pre-commit이 실행되는지 확안합니다.
```Shell
git add .
git commit -m "test"
```
