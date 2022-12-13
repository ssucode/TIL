# ngrok

### 로컬 개발환경인 localhost에서 구동 중인 웹 서비스를 외부 인터넷 환경에서 접근할 수 있도록 만들어주는 툴입니다.
> Ngrok exposes local servers behind NATs and firewalls to the public internet over secure tunnels.

- 비회원 또는 무료 회원가입: 간단한 터널링 기능을 사용
- 유료 서비스 가입: 개인 도메인, IP 제한 등 다양한 기능을 사용

#### 1. 다운로드를 받습니다.
https://ngrok.com/download
<img width="810" alt="image" src="https://user-images.githubusercontent.com/44153527/207361942-6a1547a9-236e-4118-a1d8-6e89b84a499b.png">
> 각 OS별로 다운로드 및 설치에 대해 명확히 설명되어 있습니다.

#### 2. 설치후 사용가능한 명령어를 확인해 봅니다.
```Shell
$ ngrok --help
```
#### 3. Token을 저장합니다.

> Before you can serve HTML content, you must sign up for a free ngrok account and install your authtoken.

> 기본적으로 ngrok 은 기본 세션 만료기간이 존재합니다. 기본 2시간 입니다.
> 이 세션은 만료되어 다시 ngrok을 실행해 줘야하며 재실행 시 접속 URL이 바뀌게 되어 매우 불편합니다.
> 세션 제한없이 사용하기 위해서 authtoken 을 등록합니다.
> ngrok 페이지에서 제공하는 authtoken을 복사하여 붙여넣고 실행합니다.

```Shell
$ ngrok authtoken << Your token >>
```
#### 4. 기본 명령어로 실행합니다.
테스트를 위한 로컬 서버를 실행하고 아래 명령으로 외부에서 접속 가능한 URL을 생성합니다.
```Shell
$ ngrok http << port >>
```
