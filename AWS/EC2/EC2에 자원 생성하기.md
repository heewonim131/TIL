# EC2에 자원 생성하기
## 1) 계정 생성
먼저 [AWS 홈페이지](https://aws.amazon.com/)에 접속하여 [계정을 생성한다.](https://www.lainyzine.com/ko/article/how-to-create-an-amazon-web-services-account/)<br>

## 2) EC2 서비스 접속
우측 상단 메뉴에서 내 계정 > AWS Management Console 클릭하여 AWS 관리 콘솔에 로그인한다.<br>
AWS 서비스 > 모든 서비스 > 컴퓨팅 > EC2 클릭하여 EC2 서비스에 접속한다.<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148719705-a135756e-a7f3-4c0d-8dbf-a157e7345fbf.png" style="width:70%; height:70%"/>

## 3) 인스턴스 시작
좌측 인스턴스 메뉴 > 인스턴스 > 우측 상단의 인스턴스 시작 클릭<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148719450-039b9e80-9324-4587-a171-bb0d3aac0b45.png" style="width:70%; height:70%"/>

## 4) 서버 선택
가장 위에 있는 Amazon Linux 서버를 선택하였다.<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148717605-d0e4fd29-ebe8-43e8-a3ef-2ce5643f8e77.png" style="width:70%; height:70%"/>

선택된 항목 그대로 두고, 검토 및 시작 클릭<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148718166-a35e1f24-c2f0-4c9e-8b84-f669b3e558a7.png" style="width:70%; height:70%"/>

## 5) 보안 그룹 생성
스크롤을 내려보면 보안 그룹 구성 항목이 있다.<br>
보안 그룹 구성 편집을 클릭히여 새 보안 그룹을 생성한다.<br>
그룹 이름과 설명을 입력한 뒤, 검토 및 시작 클릭<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148718418-18381f51-7935-4688-ad97-a9a649421050.png" style="width:70%; height:70%"/>

## 6) 키 페어 생성
마지막으로 아래 시작하기를 클릭하면 창이 하나 뜨는데, 기존 키 페어가 없으므로 새 키 페어를 생성해준다.<br>
이 때, **우측의 '키 페어 다운로드'를 꼭 클릭 !** 하여 파일을 저장해야 한다.<br>
다운로드가 완료되면 인스턴스를 시작한다.<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148718727-1118390f-0ab4-4dfc-ada6-170c8e53d762.png" style="width:70%; height:70%"/>

## 7) 인스턴스 생성 완료
인스턴스 생성이 완료되었다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148719267-4f13aab0-2019-4134-b9e0-b13d01c613fb.png" style="width:70%; height:70%"/>
<br>인스턴스 Name이 비었으므로 Heewon으로 설정해 주었다.<br><br>
<img src="https://user-images.githubusercontent.com/92259017/148719329-073a310a-71a2-4ed9-8da0-92a224eaaab7.png" style="width:70%; height:70%"/>

## 참고자료
- [AWS 계정 생성하는 방법 by lainyzine](https://www.lainyzine.com/ko/article/how-to-create-an-amazon-web-services-account/)
- [EC2 인스턴스 생성하기 by 꽁담](https://mozi.tistory.com/461?category=1154728)

