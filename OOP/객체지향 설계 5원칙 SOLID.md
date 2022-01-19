# 객체지향 설계 5원칙 SOLID
## 응집도와 결합도
좋은 소프트웨어 설계를 위해서는 결합도(coupling)는 낮추고 응집도(cohesion)는 높여야 한다.
#### 결합도
모듈(클래스) 간의 상호 의존 정도를 나타내는 지표로서, 결합도가 낮으면 모듈 간의 상호 의존성이 줄어들어서 객체의 재사용 및 유지보수가 용이하다.
#### 응집도
하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용 및 유지보수가 용이하다.

## 1. SRP(Single Responsibility Principle) 단일 책임 원칙
어떠한 클래스를 변경해야 하는 이유는 한 가지 뿐이어야 한다.

객체가 가진 기능에만 집중할 수 있도록, 응집도를 높이기 위해서 클래스를 분리해야 한다.

<img src="https://user-images.githubusercontent.com/92259017/150065593-133a532b-19b1-40d2-8550-91b39691157b.png" style="width: 40%; height: 40%">

<img src="https://user-images.githubusercontent.com/92259017/150065650-e8f2d2d1-57ee-4319-9ab0-43be1b4964a5.png" style="width: 40%; height: 40%">

## 2. OCP(Open-Closed Principle) 개방 폐쇄 원칙
자신의 확장에는 열려있고, 변화에 대해서는 닫혀 있어야 한다.

상위 클래스 또는 인터페이스를 중간에 둠으로써, 자신의 변화에 대해서는 폐쇄적이지만 인터페이스는 외부의 변화에 대해서 확장을 개방해 줄 수 있다.

<img src="https://user-images.githubusercontent.com/92259017/150070035-9574a2b1-182b-4e69-9cba-61dae0b39f7c.png" style="width: 60%; height: 60%">

## 3. LSP(Liskov Substitution Principle) 리스코프 치환 원칙
서브 타입은 언제나 자신의 상위 타입으로 교체될 수 있어야 한다.
<img src="https://user-images.githubusercontent.com/92259017/150070217-12ca0158-e1e2-4053-88e8-22c86de30d3c.png" style="width: 60%; height: 60%">

## 4. ISP(Interface Segregation Principle) 인터페이스 분리 원칙
클라이언트는 자신이 사용하지 않는 메서드와 의존 관계를 맺으면 안 된다.

자전거는 자전거 길 안내만 하고, 자동차는 자동차 길 안내만 할 수 있도록 분리한다.
<img src="https://user-images.githubusercontent.com/92259017/150070606-2d7f76de-46ff-49e6-89a7-628a2ba45035.png" style="width: 60%; height: 60%">

## 5. DIP(Dependency Inversion Principle) 의존 역전 원칙
자신보다 변하기 쉬운 것에 의존하지 않는다.

<img src="https://user-images.githubusercontent.com/92259017/150070673-ea1af999-4f52-4de3-a766-f18b98f88376.png" style="width: 60%; height: 60%">
<img src="https://user-images.githubusercontent.com/92259017/150070706-623d65ae-25e7-4400-9238-7b4533529767.png" style="width: 60%; height: 60%">

옷이라는 인터페이스가 들어오면서 사람도, 계절별 옷들도 옷에 의존하는 의존 역전이 일어난다.
