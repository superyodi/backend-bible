# Cache

애플리케이션,서버,웹사이트,브라우저가 요청을 받았을 때 보다 빠르게 로딩될 수 있도록 임시로 파일이나 데이터를 저장하는 메모리.

## Caching

데이터가 요청될 때마다 새로운 데이터를 생성하지 않고 자주 요청되는 데이터를 저장해놓는 것.



## Website Caching

### Process

1. 브라우저가 DNS 서버에서 웹 주소에 해당하는 IP 주소를 찾는다.(DNS Lookup)
2. 웹사이트의 복사본을 서버에 요청한다.
3. 서버가 요청을 승인하면 클라이언트에게 200 응답을 한다.
4. 이후 서버는 데이터 패킷이라고 불리는 작은 단위로 웹사이트의 파일을 브라우저에 보낸다.
5. 브라우저는 받은 데이터 패킷들을 모아서 완전한 웹 페이지를 사용자에게 보여준다.



- 이 과정은 복잡하고 브라우저가 서버에 같은 요청을 반복하기 때문에 시간낭비이다.
- 사용자가 항상 새로운 요청을 보내는 것은 안좋은 사용자경험으로 이어진다.
- **Website Caching** 은 웹페이지의 복사본을 임시적인 공간에 저장함으로서 사용자의 요청에 대한 속도를 높여준다.
- cache는 많은 파일을 저장할 수 없다.



### Working Process

1. 사용자는 브라우저에서 자원에 대한 웹페이지를 서버에 요청한다. (이 자원은 웹 주소이다.)
2. 브라우저, CDN, 또는 서버 cache는 요청받은 웹페이지에 대한 복사본이 존재하는지 확인한다.
3. cache가 사용가능한지 확인하면서 사용자는 웹 페이지를 요청하고 그 결과는 두가지로 나뉠 수 있다.
   1. Cache Hit
      - 요청받은 웹페이지의 복사본이 cache에 저장되어있다. 이것은 cache hit 응답을 만들고 cache의 자원은 사용자에게 전달된다.
   2. Cache Miss
      - 요청받은 웹페이지에 대한 복사본이 cache에 저장되어있지 않다. 브라우저는 main server에 새로운 요청을 보낸다.
4. 웹페이지가 cache된다면 그 브라우저는 그것이 지워질때까지 해당 버전을 전달한다.



## Types of Website Caching

### Server-side Caching

- 사용자가 웹페이지에 처음 요청했을 때 웹 사이트는 서버에 해당 정보를 요청한다.
- 다음 사용자가 다시 요청했을 때 서버는 새로 데이터를 생성하지 않고 저장되어 있는 데이터를 보낸다.
- 이 과정은 같은 요청에 대해서 비용이 많이 드는 DB operation을 줄일 수 있다.
- 정적인 웹사이트에 사용하기 좋다.



####  - Object Caching

- Database query 결과를 포함하는 과정이다.
- 같은 요청에 대해 쉽게 처리할 수 있다.
- db에 여러번 접근하지 않을 수 있다.

#### - Opcode Caching

- PHP에서 사용한다.

#### - CDN Caching

- CDN(Content Delivery Network)
- 전 세계 곳곳에 웹 사용자들에게 자원을 빠르게 전달하기 위한 서버가 분포되어 있다.
- 웹 사이트의 내용이 등록된 CDN provider에 지나가면 해당 서버는 그 웹 사이트의 복사본을 저장한다.
- 사용자가 웹사이트를 재방문했을 때 사용자에게 가장 가까운 서버가 웹사이트의 복사본을 전달한다.



#### 단점

- High Latency
- latency는 사용자의 요청과 웹 애플리케이션의 응답 사이 지연이다.
- latency는 데이터 패킷이 자원으로부터 목적지까지 가는 총 시간이다.
- 서버 사이드 캐시는 모든 요청이 브라우저에서 서버로 갔다 와야 하기 때문에 high latency가 일어날 수 있다.
- 첫번재 connection이 생기면, 서버가 전체 페이지를 다시 생성할 일은 없지만 저장된 페이지에 변화가 생긴다면 서버는 이전 버전을 지우고 다시 생성해야 한다.
- 서버 사이드 캐시는 항상 데이터를 처리해야 하진 않지만 저장된 캐시의 상태를 먼저 확인해야 한다.



### Client-Side Caching

- Client-side caching(browser caching)은 웹페이지의 복사본을 브라우저 메모리에 저장하는 방식이다.
- 브라우저 메모리는 사용자의 기기에 위치하기 때문에 브라우저가 웹페이지의 복사본을 가지고 있을 수 있다.
- Safari, Microsoft Edge, Google Chrome 등과 같은 브라우저들은 그들이 설치된 어느 기기에나 캐시 메모리를 가질 수 있다.
- HTML, 이미지, CSS 나 다른 멀티미디어 파일들을 저장할 수 있다.
- 이 메모리는 사용자의 캐시 메모리에 제한되기 때문에 적은 양의 데이터만 저장할 수 있고, 사용자가 캐시를 지운다면 다시 정보를 가져와야한다.
- 서버에서의 로딩을 줄이기 때문에 동적, 정적인 웹사이트 모두에서 client-side caching은 latency와 server crash 문제를 해결할 수 있다.



#### Browser Request Caching

- 가장 오래되고 흔하게 쓰이는 방식이다.
- 브라우저 캐싱 요청이 들어왔을 때, 대부분의 캐싱은 웹사이트 코드의 헤더 부분에서 만들어진다.
- 이것은 웹사이트 로딩 시간에 영향을 주는 FCP(First Contentful Paint)와 LCP(Largest Contentful Paint) 같은 metrics? 때문이다.
- 다음은 웹 사이트 캐싱에서의 몇가지 헤더와 역할이다.
  - Expires : 캐시 데이터의 expiration date를 만든다
  - Pragma(no-cache) : 브라우저에 캐시되는 내용의 유형을 제어한다. 특정 내용물은 캐시되면 안된다는 것을 알려준다.
  - Etag(entity tag) : 캐시된 웹페이지나 파일의 버전을 제어하기 위한 해시값을 만든다. 
  - If-Modified-Since : 캐시된 데이터가 수정된 시간을 알려준다.
  - Last-Modified : 캐시된 데이터가 수정되었는지 확인하고 응답을 if-modified-since 헤더에 보낸다.
  - Cache-Control : 데이터가 브라우저 메모리에 캐시되어야 하는지 확인하는 주요 header이다.
    - 사용자가 브라우저를 통해 서버에 데이터(내용물)을 요청한다.
    - 서버가 응답한다.
    - Cache-Control header가 사용자의 응답이 브라우저 메모리에 저장되어야 하는지 요청?한다.
      - yes면 cache-control은 얼마나 저장되어야 하는지와 함께 응답한다.
      - no면 저장하지 않는다.

#### Javascript/AJAX Caching

- 페이지 전체를 refresh하는 것이 아닌, 동적인 부분만 바꾼다.

#### HTML 5 Caching

##### * 참고

https://edgemesh.com/blog/difference-between-server-side-caching-and-client-side-caching-and-which-is-good-for-your-website