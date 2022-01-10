# EC2에 서비스 배포하기
## 목차
  - [EC2란?](https://github.com/heewonim131/TIL/tree/main/AWS/02#1-EC2란)
  - [EC2에 자원 생성하기](https://github.com/heewonim131/TIL/tree/main/AWS/02#2-EC2에-자원-생성하기)
  - [EC2에 애플리케이션 배포하기](https://github.com/heewonim131/TIL/tree/main/AWS/02#3-EC2에-애플리케이션-배포하기)
  - [EC2 자원 삭제하기](https://github.com/heewonim131/TIL/tree/main/AWS/02#4-EC2-자원-삭제하기)
  - [참고자료](https://github.com/heewonim131/TIL/tree/main/AWS/02#참고자료)

## 1. EC2란?
EC2는 Elastic Compute Cloud의 약자로, 물리적 자원을 제공하는 AWS의 대표적인 서비스이다.<br>
CPU, 메모리 등 자원을 필요한 만큼 대여하여 서버를 구축하고, 내부에 논리적인 애플리케이션을 배포할 수 있는 공간이다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148725792-b6c69e56-a72a-4f3c-ada9-c834acb087e6.png" style="width:50%; height:50%"/>

## 2. EC2에 자원 생성하기
### 2-1) 계정 생성
먼저 [AWS 홈페이지](https://aws.amazon.com/)에 접속하여 [계정을 생성한다.](https://www.lainyzine.com/ko/article/how-to-create-an-amazon-web-services-account/)<br>

### 2-2) EC2 서비스 접속
우측 상단 메뉴에서 내 계정 > AWS Management Console 클릭하여 AWS 관리 콘솔에 로그인한다.<br>
AWS 서비스 > 모든 서비스 > 컴퓨팅 > EC2 클릭하여 EC2 서비스에 접속한다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148719705-a135756e-a7f3-4c0d-8dbf-a157e7345fbf.png" style="width:70%; height:70%"/>

### 2-3) 인스턴스 시작
좌측 인스턴스 메뉴 > 인스턴스 > 우측 상단의 인스턴스 시작 클릭<br>
<img src="https://user-images.githubusercontent.com/92259017/148719450-039b9e80-9324-4587-a171-bb0d3aac0b45.png" style="width:70%; height:70%"/>

### 2-4) 서버 선택
가장 위에 있는 Amazon Linux 서버를 선택하였다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148717605-d0e4fd29-ebe8-43e8-a3ef-2ce5643f8e77.png" style="width:70%; height:70%"/>

선택된 항목 그대로 두고, 검토 및 시작 클릭<br>
<img src="https://user-images.githubusercontent.com/92259017/148718166-a35e1f24-c2f0-4c9e-8b84-f669b3e558a7.png" style="width:70%; height:70%"/>

### 2-5) 보안 그룹 생성
스크롤을 내려보면 보안 그룹 구성 항목이 있다.<br>
보안 그룹 구성 편집을 클릭히여 새 보안 그룹을 생성한다.<br>
그룹 이름과 설명을 입력한 뒤, 검토 및 시작 클릭<br>
<img src="https://user-images.githubusercontent.com/92259017/148718418-18381f51-7935-4688-ad97-a9a649421050.png" style="width:70%; height:70%"/>

### 2-6) 키 페어 생성
마지막으로 아래 시작하기를 클릭하면 창이 하나 뜨는데, 기존 키 페어가 없으므로 새 키 페어를 생성해준다.<br>
이 때, **우측의 '키 페어 다운로드'를 꼭 클릭 !** 하여 파일을 저장해야 한다.<br>
다운로드가 완료되면 인스턴스를 시작한다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148718727-1118390f-0ab4-4dfc-ada6-170c8e53d762.png" style="width:70%; height:70%"/>

### 2-7) 인스턴스 생성 완료
인스턴스 생성이 완료되었다.<br>
인스턴스 Name이 비었으므로 Heewon으로 설정해 주었다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148719267-4f13aab0-2019-4134-b9e0-b13d01c613fb.png" style="width:70%; height:70%"/>
<img src="https://user-images.githubusercontent.com/92259017/148719329-073a310a-71a2-4ed9-8da0-92a224eaaab7.png" style="width:70%; height:70%"/>

## 3. EC2에 애플리케이션 배포하기
간단한 Node.js 애플리케이션을 만들어 배포해 보자.

### 3-1) Windows 10에서 EC2 인스턴스 접속하기
- 하단의 인스턴스 요약에서 퍼블릭 IPv4 주소를 복사한다.<br>
  <img src="https://user-images.githubusercontent.com/92259017/148720615-2ef45fd6-b38b-4d63-9ed9-c8a5ab3ad7d5.png" style="width:70%; height:70%"/>

- 터미널(ex. cmd, Windows PowerShell) 실행<br>

  - [SSH 활성화 여부를 확인하고, 폴더 권한을 부여해야 한다.](https://www.overtop.co.kr/361)<br>
  
  - keyPair 파일이 있는 경로(경로에 한글이 포함되어 있으면 오류가 발생한다.)로 이동하여 다음의 명령어를 입력한다.<br>
  ```
  ssh -i [키페어 이름].pem ec2-user@[퍼블릭 IPv4 주소]
  ```
  - yes를 입력하면 다음과 같이 접속이 완료된 것을 확인할 수 있다.<br><br>
  <img src="https://user-images.githubusercontent.com/92259017/148723723-bb6a9d8d-5f4d-42d7-9a74-d0a7274f040e.png" style="width:70%; height:70%"/>

### 3-2) 인스턴스에 Node.js 설치
- [Node Version Manager](https://github.com/nvm-sh/nvm)에서 여러 버전의 Node.js를 설치할 수 있다.
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
  
### 3-3) Node.js 애플리케이션 만들기
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

### 3-4) Node.js 앱 실행하기
1. 터미널에서 실행
    - 기존 터미널에서 index.js 파일을 로드한다.<br>
    ```
    node index.js
    ```
    <img src="https://user-images.githubusercontent.com/92259017/148740848-a87e9f25-ca8e-4c45-a417-ab3e75e75a18.png" style="width:70%; height:70%"/><br>

    - 새로운 터미널을 실행하여 EC2 인스턴스 접속(본문 3-1) 후 다음 명령어로 index.js 파일 GET 요청<br>
    ```
    curl localhost:3000
    ```
    
    - 다음과 같이 작성한 내용이 출력되는 것을 확인할 수 있다.<br>
    <img src="https://user-images.githubusercontent.com/92259017/148740901-e4f7074e-3a82-4fe0-b58a-e304268ead05.png" style="width:70%; height:70%"/><br>

    <details>
    <summary>port 연결 오류</summary><br>
    curl 명령을 실행했을 때, port 연결 오류가 발생하는 경우<br><br>
    error message:<br>
    curl: (7) Failed to connect to localhost port 3000: Connection refused<br><br>
    해결 방법: 기존 터미널에서 js 파일을 다시 로드해 본다.<br>
    </details>

2. Chrome 브라우저에서 실행



## 4. EC2 자원 삭제하기

## 참고자료
- [AWS 계정 생성하는 방법 by lainyzine](https://www.lainyzine.com/ko/article/how-to-create-an-amazon-web-services-account/)
- [EC2 인스턴스 생성하기 by 꽁담](https://mozi.tistory.com/461?category=1154728)
- [Windows PowerShell 실행하기 by 끔손](https://appia.tistory.com/409)
- [EC2 인스턴스 접속하기 by AWS-in](https://www.overtop.co.kr/361)
- [EC2 연결 시 키페어 경로 오류 by 737](https://m.blog.naver.com/7-3-7/222017188839)
