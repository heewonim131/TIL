## JWT (Json Web Token) 이란
Json 포맷을 이용하여 사용자에 대한 속성을 저장하는 Claim 기반의 Web Token이다.
JWT는 토큰 자체를 정보로 사용하는 Self-Contained 방식으로 정보를 안전하게 전달한다.

### JWT 장점
- 이미 토큰 자체가 인증된 정보이기 때문에 세션 저장소와 같은 별도의 인증 저장소가 "필수적"으로 필요하진 않다.
- 세션과는 다르게 클라이언트의 상태를 서버가 저장해두지 않아도 된다.
- signature를 공통 키 개인키 암호화를 통해 막아두었기 때문에 데이터에 대한 보완성이 향상된다.
- 다른 서비스에 이용할 수 있는 공통적인 스펙으로서 사용할 수 있다.

### JWT 단점
- Self-contained: 토큰 자체에 정보를 담고 있으므로 양날의 검이 될 수 있다. 
- 토큰 길이: 토큰의 페이로드(Payload)에 3종류의 클레임을 저장하기 때문에, 정보가 많아질수록 토큰의 길이가 늘어나 네트워크에 부하를 줄 수 있다. 
- Payload 인코딩: 페이로드(Payload) 자체는 암호화 된 것이 아니라, BASE64로 인코딩 된 것이다. 중간에 Payload를 탈취하여 디코딩하면 데이터를 볼 수 있으므로, JWE로 암호화하거나 Payload에 중요 데이터를 넣지 않아야 한다. 
- Stateless: JWT는 상태를 저장하지 않기 때문에 한번 만들어지면 제어가 불가능하다. 즉, 토큰을 임의로 삭제하는 것이 불가능하므로 토큰 만료 시간을 꼭 넣어주어야 한다. 
- Tore Token: 토큰은 클라이언트 측에서 관리해야 하기 때문에, 토큰을 저장해야 한다.

<hr>

## JWT 구조
JWT는 header, payload, signature 로 이루어지며, Base64로 인코딩 되어 표현된다. 각각의 부분은 '.' 구분자로 연결된다.
![image](https://user-images.githubusercontent.com/92259017/154797655-be1a7266-845e-4bf5-8d2a-f16aab051d1f.png)

### 1. header
header에는 토큰의 타입이나, 서명 생성에 어떤 알고리즘이 사용되었는지 저장한다.
![image](https://user-images.githubusercontent.com/92259017/154797641-5d4dbfd2-c632-42b3-8253-774838b0a012.png)
- typ: 토큰의 타입을 지정
- alg: signature를 해싱하기 위한 알고리즘 방식을 지정하며, 서명(Signature) 및 토큰 검증에 사용

### 2. payload
payload에는 클레임이라는 토큰에 필요한 정보를 key-value의 형태로 저장한다.
![image](https://user-images.githubusercontent.com/92259017/154797667-4025ff1a-7dee-4397-97ca-92fb83057b4d.png)

- #### JWT 스펙에서 지정한 claim
  - iss : Issuer 토큰을 발행한 사람(단체,사이트)이 누구인지
  - sub : Subject 무엇에 관한 토큰인지
  - aud : Audience 누구를 대상으로 한 토큰인지
  - exp : Expiration 토큰의 만료 시간은 언제인지
  - nbf : Not Before 토큰이 언제부터 유효한지
  - iat : Issued At 토큰 발행 시간
  - jti : JWT ID : 토큰 자체의 아이디
  - 그 밖에 인증에 필요하거나 대상서버에서 필요로 하는 데이터

### 3. signature
서명(Signature)은 토큰을 인코딩하거나 유효성 검증을 할 때 사용하는 고유한 암호화 코드이다.
서명(Signature)은 위에서 만든 헤더(Header)와 페이로드(Payload)의 값을 각각 BASE64로 인코딩하고,
인코딩한 값을 비밀 키를 이용해 헤더(Header)에서 정의한 알고리즘으로 해싱을 하고, 이 값을 다시 BASE64로 인코딩하여 생성한다.

![image](https://user-images.githubusercontent.com/92259017/154797688-93275a21-907a-4882-b240-f7c8ac8be35a.png)

<hr>

### 토큰에는 어떤 내용을 넣어야 할까?
- 인증에 필요한 최소한의 데이터를 넣는다.
- 비밀번호나 전화번호등을 넣는 것은 안전하지 않다.
- 서버에서 인증된 키가 아니라도 언제든 서버는 이 토큰을 열어서 그 안에 어떤 Claim 이 있는지를 볼 수 있기 때문에
  토큰은 언제든 공개할 수 있는 정보를 넣는 것이 좋다.

### 토큰을 어떻게 관리할 것인가?
- 이론적으로는 토큰을 클라이언트가 관리하게 하지만
실제로 서버는 사용자 정보 캐싱이나 토큰의 유효성 평가,
혹은 refresh 토큰 정책을 위해 서버에 토큰을 관리하기도 한다.
- 이 경우, 토큰과 사용자 정보를 관리하는 방법으로 다음과 같은 방법들을 사용하기도 한다.
  - redis, hazelcast, db 저장

## 참고
- [[Server] JWT(Json Web Token)란? by 망나니개발자](https://mangkyu.tistory.com/56)
- [JWT(Json Web Token) 알아가기 by 최진영](https://brunch.co.kr/@jinyoungchoi95/1)
