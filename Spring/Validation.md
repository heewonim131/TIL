## Validation
Java에서는 null 값에 대해서 접근하려고 할 때 null pointer exception이 발생하는데,
이러한 부분을 방지하기 위해서 미리 검증하는 과정을 의미한다.
1. 검증해야 할 값이 많은 경우 코드의 길이가 길어진다.
2. 구현에 따라서 달라질 수 있지만 Service Logic과의 분리가 필요하다.
3. 흩어져 있는 경우 어디에서 검증을 하는지 알기 어려우며 재사용의 한계가 있다.
4. 구현에 따라 달라질 수 있지만, 검증 Logic이 변경되는 경우
테스트 코드 등 참조하는 클래스에서 Logic 변경되어야 하는 부분이 발생할 수 있다.

![image](https://user-images.githubusercontent.com/92259017/150723314-f5a6a4fc-84b6-447a-8ee0-66b8b761b741.png)

### Gradle dependencies
{ implementation("org.springframework.boot:spring-boot-starter-validation") }

### Bean validation spec
https://beanvalidation.org/2.0-jsr380/
