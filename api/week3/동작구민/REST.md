# REST API

REST?
> URI(자원 좌표)를 통해 자원을 선택하고 그 자원에 대해 CRUD(Create, Read, Update, Delete) 하는것을 의미 → 자원의 표현에 의한 상태 전달을 의미

## Restful API 특징

* Client-Server 구조
    * 자원이 Server, 요청이 Client
* Stateless
    * 이전에 했던 요청이 이후 요청에 영향을 끼치면 안된다 (DB로 인한 요청 결과가 달라지는 것을 의미하진 않음)
    * 요청의 일관성을 유지시키기 위한 것으로 보임
* Cacheable
    * 대량의 요청을 해결하기 위해 캐시가 요구됨
* 계층화
    * 계층화를 통한 추상화로 문제 해결
* Interface 일관성
    * GET/POST/DELETE/UPDATE와 같은 것(?)


### 장점

* 사용하기 쉽다.
* Context를 이해할 필요 없다. (각자의 역할이 완벽한게 분리되어 있다.
    * 이러한 특성 덕분에 HTTP Protocol을 사용할 수 있다면 다양한 플랫폼에서 원하는 서비스를 쉽게 붙일 수 있다.
* 필요한 실제 데이터를 URI를 통해 쉽게 알아볼 수 있다.

### 단점
* Method 형태가 제한적이기 때문에 더 표현하고 싶어도 못하는 경우가 있다.
* 표준이 없다.

