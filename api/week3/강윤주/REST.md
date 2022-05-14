# **REST(Representational State Transfer)**

: 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것.

1. HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고,
2. HTTP Method(POST, GET, PUT, DELETE)를 통해
3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미합니다.

⇒

**자원(Resource) : HTTP URI**

**자원에 대한 행위(Verb) : HTTP Method**

**자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load**

### 특징

1. Server-Client(서버-클라이언트 구조)
2. Stateless(무상태)
3. Cacheable(캐시 처리 가능)
4. Layered System(계층화)
5. Uniform Interface(인터페이스 일관성)

장점

- HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구출할 필요가 없다.
- HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해 준다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
- Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다.
- REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악할 수 있다.
- 여러 가지 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
- 서버와 클라이언트의 역할을 명확하게 분리한다.

단점

- 표준이 자체가 존재하지 않아 정의가 필요하다.
- 사용할 수 있는 메소드가 4가지밖에 없다.
- HTTP Method 형태가 제한적이다.
- 브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 정보의 값을 처리해야 하므로 전문성이 요구된다.
- 구형 브라우저에서 호환이 되지 않아 지원해주지 못하는 동작이 많다.(익스폴로어)

**1.  URI는 동사보다는 명사를, 대문자보다는 소문자를 사용하여야 한다.**

**2. 마지막에 슬래시 (/)를 포함하지 않는다.**

**3. 언더바 대신 하이폰을 사용한다.**

**4. 파일확장자는 URI에 포함하지 않는다.**

**5. 행위를 포함하지 않는다.**

### 기타

- REST는 HTTP 위에서 만들어졌다.
- REST는 소프트웨어 아키텍처 스타일
- HTTP는 텍스트 기반의 통신 규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜



참고 URL : https://velog.io/@springer/1-RESTful-%EC%9B%B9%EC%84%9C%EB%B9%84%EC%8A%A4