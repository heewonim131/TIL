# REST API
(Representational State Transfer, 자원의 상태 전달)

다음 6가지 아키텍처를 잘 지켜야 RESTful한 API라고 할 수 있다.
1. #### Client, Server<br>
    클라이언트와 서버가 서로 독립적으로 분리되어 있어야 한다.

2. #### Stateless<br>
    요청에 대해서 클라이언트의 상태를 서버에 저장하지 않아야 한다.<br>
서버가 요청을 기억하지 않기 때문에 모든 요청을 새롭게 보내야 한다.

3. #### Cache<br>
    클라이언트는 서버의 응답을 Cache(임시저장) 할 수 있어야 한다.<br>
클라이언트가 Cache를 통해서 응답을 재사용 할 수 있어야 하며, 이를 통해 서버의 부하를 낮춘다.

4. #### 계층화 (Layered System)<br>
    서버와 클라이언트 사이에, 방화벽, 게이트웨이, Proxy Server 등 추가될 수 있기 때문에<br>
다양한 계층 형태로 구성이 가능해야 하며, 이를 확장할 수 있어야 한다.

5. #### 인터페이스 일관성<br>
    인터페이스의 일관성을 지키고, 아키텍처를 단순화해 작은 단위로 분리해야 한다.<br>
클라이언트, 서버가 독립적으로 개선될 수 있어야 한다.<br>
어느 한 쪽이 변경되는 것에 영향을 받지 않도록 일관성 있게 구성되어야 한다.

6. #### Code on Demand (Optional 일수도)<br>
    자바 스크립트, 자바 애플릿, 플래시 등 특정한 기능을 서버로부터 클라이언트가 전달받아서<br>
클라이언트에서 코드를 실행할 수 있어야 한다.

<hr>

## 인터페이스 일관성
다음의 인터페이스 일관성이 잘 지켜졌는지에 따라 REST를 잘 사용했는지 판단할 수 있다.
1. #### 자원의 식별
    웹 기반의 REST에서는 리소스 접근을 할 때 URI를 사용한다.<br>
    URI에 자원을 식별할 수 있는 정보가 담겨 있어야 한다.<br>
    https://foo.co.kr/user/100<br>
    Resource : user<br>
    식별자 : 100<br>
    위의 URI는 100번째 user를 나타낸다.

2. #### 메시지를 통한 리소스 조작
    Web에서는 다양한 방식으로 데이터를 전달하는데, 많이 사용하는 방식은 HTML, XML, JSON, TEXT 등이 있다.<br>
    데이터 타입을 알려주기 위해 HTTP Header 부분에 content-type을 통해 타입을 지정해 줄수 있다.<br>
    리소스 조작을 위해 데이터 전체를 전달 하지 않고, 별도의 메시지 형태로 데이터를 주고 받으며 client-server가 독립적으로 확장 가능하도록 한다.

3. #### 자기 서술적 메시지
    요청하는 데이터가 어떻게 처리 되어야 하는지 충분한 데이터를 포함할 수 있어야 한다.<br>
    HTTP 기반의 REST에서는 HTTP Method, Header 정보, URI에 포함되는 정보로 표현할 수 있다.<br>
    |HTTP Method|URI|요청|
    |:--|:--|:--|
    |GET|https://foo.co.kr/user/100|사용자의 정보 요청|
    |POST|https://foo.co.kr/user|사용자 정보 생성|
    |PUT|https://foo.co.kr/user|사용자 정보 생성 및 수정|
    |DELETE|https://foo.co.kr/user/100|사용자 정보 삭제|
    
    그 외에 담지 못한 정보들은 URI의 메시지를 통해 표현한다.

4. #### 애플리케이션 상태에 대한 엔진으로서 하이퍼미디어
    REST API를 개발할 때 단순히 Client 요청에 대한 데이터만 응답을 해주는 것이 아닌<br>
    관련된 리소스에 대한 Link 정보까지 같이 포함이 되어야 한다.<br>
    이러한 조건들을 잘 갖춘 경우 REST Ful 하다고 표현하고, 이를 REST API라고 한다.

<hr>

## URI 설계 패턴
### URI (Uniform Resource Identifier)
인터넷에서 특정 자원을 나타내는 유일한 주소 값. 응답은 달라질 수 있다.<br>
요청 : https://www.fastcampus.co.kr/resource/sample/1<br>
응답 : fastcampus.pdf, fastcampus.docx

### URL (Uniform Resource Locator)
인터넷 상에서의 자원, 특정 파일이 어디에 위치하는지 식별하는 주소.<br>
요청 : https://www.fastcampus.co.kr/fastcampus.pdf<br>
URL은 URI의 하위 개념 이다.

### URI 설계 원칙 (RFC-3986)
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
