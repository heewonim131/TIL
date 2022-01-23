## URI (Uniform Resource Identifier)
인터넷에서 특정 자원을 나타내는 유일한 주소 값. 응답은 달라질 수 있다.<br>
요청 : https://www.fastcampus.co.kr/resource/sample/1<br>
응답 : fastcampus.pdf, fastcampus.docx

## URL (Uniform Resource Locator)
인터넷 상에서의 자원, 특정 파일이 어디에 위치하는지 식별하는 주소.<br>
요청 : https://www.fastcampus.co.kr/fastcampus.pdf<br>
URL은 URI의 하위 개념 이다.

## URI 설계 원칙 (RFC-3986)
- 슬래시 구분자(/)는 계층 관계를 나타내는 데 사용한다.<br>
- URI 마지막 문자로 슬래시(/)는 포함하지 않는다.<br>
- 하이픈(-)은 URI 가독성을 높이는 데 사용한다.<br>
- 밑줄(_)은 사용하지 않는다.<br>
- URI 경로에는 소문자가 적합하다.<br>
- 파일 확장자는 URI에 포함하지 않는다.<br>
- 프로그래밍 언어에 의존적인 확장자를 사용하지 않는다.<br>
    .../ **lesson.do** -> .../lesson
    
- 구현에 의존적인 경로를 사용하지 않는다.<br>
    .../ **servlet** /lesson -> .../lesson

- 세션 ID를 포함하지 않는다.<br>
    .../lesson **?session-id=abcd** -> .../lesson
    
- 프로그래밍 언어의 Method명을 이용하지 않는다.<br>
    .../lesson **?action=intro** -> .../lesson

- 명사에 단수형 보다는 복수형을 사용한다.<br>

- 컨트롤러 이름으로는 동사나 동사구를 사용한다.<br>
  .../lesson/ **re-order**
  
- 경로 부분 중 변하는 부분은 유일한 값으로 대체한다.<br>
    .../user/ **{user-id}** -> .../user/ **1**
    
- URI에 CRUD 기능을 나타내지 않는다.<br>
    .../user/1/ **READ** -> .../user/1
    
- URI를 Query Parameter로 디자인하여 정보를 나타낸다.<br>
    .../lesson **?chapter=2**
    
- URI 쿼리는 컬렉션의 결과를 페이지로 구분하여 나타내는 데 사용한다.<br>
    .../lesson **?chapter=2&page=1&sort=asc**
    
- API에 있어서 서브 도메인은 일관성 있게 사용해야 한다.<br>
    https://api.fastcampus.co.kr
    https://api-fastcampus.co.kr

- 클라이언트 개발자 포털 서브 도메인은 일관성 있게 만든다.<br>
    https://dev-fastcampus.co.kr
    https://developer-fastcampus.co.kr
