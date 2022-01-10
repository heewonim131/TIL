# EC2에 서비스 배포하기

## EC2란?
EC2는 Elastic Compute Cloud의 약자로, 물리적 자원을 제공하는 AWS의 대표적인 서비스이다.<br>
CPU, 메모리 등 자원을 필요한 만큼 대여하여 서버를 구축하고, 내부에 논리적인 애플리케이션을 배포할 수 있는 공간이다.

## EC2에 자원 생성하기
먼저 [AWS 홈페이지](https://aws.amazon.com/)에 접속하여 계정 생성을 생성한다.<br>
우측 상단 메뉴에서 내 계정 > AWS Management Console 클릭하여 AWS 관리 콘솔에 로그인한다.<br>

AWS 서비스 > 모든 서비스 > 컴퓨팅 > EC2<br>
<img src="https://user-images.githubusercontent.com/92259017/148719705-a135756e-a7f3-4c0d-8dbf-a157e7345fbf.png" style="width:70%; height:70%"/>

좌측 메뉴 인스턴스 > 인스턴스 클릭 > 우측 상단의 인스턴스 시작<br>
<img src="https://user-images.githubusercontent.com/92259017/148719450-039b9e80-9324-4587-a171-bb0d3aac0b45.png" style="width:70%; height:70%"/>

가장 위에 있는 Amazon Linux 서버 선택<br>
<img src="https://user-images.githubusercontent.com/92259017/148717605-d0e4fd29-ebe8-43e8-a3ef-2ce5643f8e77.png" style="width:70%; height:70%"/>

선택된 항목 그대로 > 검토 및 시작<br>
<img src="https://user-images.githubusercontent.com/92259017/148718166-a35e1f24-c2f0-4c9e-8b84-f669b3e558a7.png" style="width:70%; height:70%"/>

스크롤을 내려보면 보안 그룹 구성 항목이 있다.<br>
보안 그룹 구성 편집 > 새 보안 그룹 생성 > 이름, 설명 설정 > 검토 및 시작<br>
<img src="https://user-images.githubusercontent.com/92259017/148718418-18381f51-7935-4688-ad97-a9a649421050.png" style="width:70%; height:70%"/>

마지막으로 아래 시작하기를 클릭하면 창이 하나 뜨는데, 기존 키 페어가 없으므로 새 키 페어를 생성해준다.<br>
새 키 페어 생성 선택 > 키 페어 이름 설정 > **우측에 '키 페어 다운로드'를 꼭 클릭 !** > 인스턴스 시작<br>
<img src="https://user-images.githubusercontent.com/92259017/148718727-1118390f-0ab4-4dfc-ada6-170c8e53d762.png" style="width:70%; height:70%"/>

인스턴스 생성이 완료되었다.<br>
인스턴스 Name이 비었으므로 Heewon으로 설정해 주었다.<br>
<img src="https://user-images.githubusercontent.com/92259017/148719267-4f13aab0-2019-4134-b9e0-b13d01c613fb.png" style="width:70%; height:70%"/>
<img src="https://user-images.githubusercontent.com/92259017/148719329-073a310a-71a2-4ed9-8da0-92a224eaaab7.png" style="width:70%; height:70%"/>
