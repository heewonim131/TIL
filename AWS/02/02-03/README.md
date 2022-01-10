# EC2에 애플리케이션 배포하기
간단한 Node.js 애플리케이션을 만들어 배포해 보자.

## 1) Windows 10에서 EC2 인스턴스 접속하기
- 하단의 인스턴스 요약에서 퍼블릭 IPv4 주소를 복사한다. (계속해서 쓰이니 메모장에 복사해놓자.)<br><br>
  <img src="https://user-images.githubusercontent.com/92259017/148720615-2ef45fd6-b38b-4d63-9ed9-c8a5ab3ad7d5.png" style="width:70%; height:70%"/>

- [SSH 활성화 여부를 확인하고, 폴더 권한을 부여해야 한다.](https://www.overtop.co.kr/361)

- 위의 작업을 완료했으면 터미널(ex. cmd, Windows PowerShell)을 실행한다.

- keyPair 파일이 있는 경로로 이동하여 아래의 명령어를 입력한다.<br>(경로에 한글이 포함되어 있으면 오류가 발생한다.)
  ```
  ssh -i [키페어 이름].pem ec2-user@[퍼블릭 IPv4 주소]
  ```
- yes를 입력하면 다음과 같이 접속이 완료된 것을 확인할 수 있다.<br><br>
  <img src="https://user-images.githubusercontent.com/92259017/148723723-bb6a9d8d-5f4d-42d7-9a74-d0a7274f040e.png" style="width:70%; height:70%"/>

## 2) 인스턴스에 Node.js 설치
[Node Version Manager](https://github.com/nvm-sh/nvm)에서 여러 버전의 Node.js를 설치할 수 있다.
- nvm 설치<br>
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```
```
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

- Node.js LTS 버전 설치<br>
```
nvm install --[버전이름]
```
```
nvm use --[버전이름]
```
<img src="https://user-images.githubusercontent.com/92259017/148733283-22d367c4-4b3b-495b-9367-0da1d454d4e0.png" style="width:70%; height:70%"/>
  
## 3) Node.js 애플리케이션 만들기
- 'app' 폴더 생성 후 이동<br>
```
mkdir app
```
```
cd app
```

- express 패키지 설치<br>
```
npm i -S express
```
<img src="https://user-images.githubusercontent.com/92259017/148733901-dc63620c-99df-475a-a178-519e3849d87b.png" style="width:70%; height:70%"/>

- Node.js 앱 작성

```
vi index.js
```

<img src="https://user-images.githubusercontent.com/92259017/148735483-36773289-e5ab-45d2-a4d7-ada1dd229321.png" style="width:70%; height:70%"/><br>
위와 같이 파일 작성을 완료했다면,<br>
Esc -> Shift + :(콜론) -> wq(저장하고 닫기) 입력 후 Enter를 쳐서 빠져나온다.

## 4) Node.js 앱 실행하기
### 4-1) 터미널에서 실행

  - 기존 터미널에서 index.js 파일을 로드한다.
  ```
  node index.js
  ```
  <img src="https://user-images.githubusercontent.com/92259017/148740848-a87e9f25-ca8e-4c45-a417-ab3e75e75a18.png" style="width:70%; height:70%"/><br>

  - 새로운 터미널을 실행하여 EC2 인스턴스에 접속한 뒤, (본문 3-1)<br>
  아래의 명령어를 입력하여 index.js 파일을 GET 요청한다.<br>
  ```
  curl localhost:3000
  ```

  - 다음과 같이 작성한 내용이 출력되는 것을 확인할 수 있다.

  <img src="https://user-images.githubusercontent.com/92259017/148740901-e4f7074e-3a82-4fe0-b58a-e304268ead05.png" style="width:70%; height:70%"/><br>

  <details>
  <summary>port 연결 오류</summary><br>
  curl 명령을 실행했을 때, port 연결 오류가 발생하는 경우<br><br>
  error message:<br>
  curl: (7) Failed to connect to localhost port 3000: Connection refused<br><br>
  해결 방법: 기존 터미널에서 js 파일을 다시 로드해 본다.<br>
  </details>


### 4-2) Chrome 브라우저에서 실행

  외부 브라우저에서 실행할 수 있도록 3000번 port를 오픈해주어야 한다.<br>
  - 보안 탭의 보안 그룹 링크를 클릭한다.
  <img src="https://user-images.githubusercontent.com/92259017/148744373-227acb9a-134d-4348-9eb3-0b386e9eae44.png" style="width:70%; height:70%"/>

  - 인바운드 규칙 편집을 클릭한다.
  <img src="https://user-images.githubusercontent.com/92259017/148744573-bdd82f14-4a73-4636-9015-45359ef40b38.png" style="width:70%; height:70%"/>

  - 다음과 같이 규칙을 추가하고 저장한다.
  <img src="https://user-images.githubusercontent.com/92259017/148745137-3bfaf89f-0227-4c3c-903f-cc4a02338835.png" style="width:70%; height:70%"/>

  - [퍼블릭 IPv4 주소]:3000 페이지를 로드하면 index.js 파일이 잘 실행되는 것을 볼 수 있다.
  <img src="https://user-images.githubusercontent.com/92259017/148746321-60a3b361-a7e8-44a4-99ae-8173fee8d037.png" style="width:70%; height:70%"/>

## 참고자료
- [Windows PowerShell 실행하기 by 끔손](https://appia.tistory.com/409)
- [EC2 인스턴스 접속하기 by AWS-in](https://www.overtop.co.kr/361)
- [EC2 연결 시 키페어 경로 오류 by 737](https://m.blog.naver.com/7-3-7/222017188839)
- [[NodeJS] Terminal에서 node index.js를 치면 무슨일이 일어날까? by Byeongin Yoon](https://medium.com/@rpf5573/terminal%EC%97%90%EC%84%9C-node-index-js%EB%A5%BC-%EC%B9%98%EB%A9%B4-%EB%AC%B4%EC%8A%A8%EC%9D%BC%EC%9D%B4-%EC%9D%BC%EC%96%B4%EB%82%A0%EA%B9%8C-af6c75ee4800)
