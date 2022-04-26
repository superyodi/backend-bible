# REST API





> restful api design guidelines





> 목차
>
> 1. 서론
> 2. REST
> 4. RESTful
> 5. 프로젝트에 적용해보자





## 서론

REST 는 어떤 배경에서 탄생하게 되었을까?

SPA, 웹 브라우저 외 클라이언트가 탄생하는 등 기술적 발전에 따라 서버에서 완성해서 html을 통째로 제공하던 기존의 방식에 한계를 느끼게 되었다. 

따라서 클라이언트의 요청에 따라 필요한 자원에 대한 요청만 제공하는 REST 아키텍쳐가 탄생하게 되었다. 





### SPA(Single Page Application)

![SPA(Single Page Application)](https://scand.com/wp-content/uploads/2019/05/bp062-difference.jpg)







#### Server-side Rendering

*Traditional Page Lifecycle*

+ 서버가 클라이언트 요청에 완성된 페이지(HTML)를 응답한다
+ 화면을 변경하기 위해서는 새로운 요청이 필요
+  ex) JSP, Thymeleaf



#### Client-side Rendering

*SPA Lifecycle*

+ 서버는 최초 일부 HTML만을 응답 (optional)
+ 클라이언트에서 js를 통해 나머지 HTML을 랜더링
+ 클라이언트가 AJAX 등을 통해 서버에 데이터를 요청 (**API**)
+ 서버는 클라이언트 요청에 데이터(JSON 등)를 응답(**API**)
+ <u>화면은 클라이언트 단에서 동적으로 변경됨</u>
+ ex) React, Vue, Angular





## REST

+ 정의
  + *Representational State Transfer*
  + 자원을 이름으로 구분해서 해당 자원의 상태를 주고 받는 모든 것 
  + 분산시스템 설계를 위한 아키텍처 스타일 

+ 탄생 배경 

  **확장성, 분산시스템, 데이터 소모량 감소**

  <u>클라이언트가 요청한 데이터만 보내주는건 어떨까?</u>

  ==> 어떻게?

  기존에 사용하던 HTTP 메소들을 동사로, url을 이름으로 정해서 자원의 생태를 주고 받으면 되잖음!

+ 6개의 제약들

  + Uniform Interface

    HTTP 표준만 따른다면 **특정 언어나 기술에 종속되지 않고 모든 플랫폼에서 사용**할 수 있으며

    URI로 지정한 리소스에 대한 조작이 가능한 아키텍처 스타일 

  + Stateless, 무상태성

    작업을 위한 상태정보를 따로 저장하고 관리하지 않는다. 

    API서버는 들어오는 요청만을 단순하게 처리하면 된다. 

    ==> 서비스의 자유도가 높아지고 구현이 단순해진다. 

  + Cacheable, 캐시 가능

    HTTP라는 기존 웹 표준을 그대로 사용하기 때문에 웹에서 사용하는 기존 인프라를 그대로 활용할 수 있다. 

    따라서 HTTP가 가진 캐싱기능을 적용할 수 있다. 

  + Clinet-Server

    클라이언트 - 서버 구조로 되어있다. 

  + Layered System, 계층형 구조

    다중 계층으로 구성될 수 있다.

    로드밸런싱, 암호화 계층, 보안 등을 추가해 구조상의 유연성을 둘 수 있다. 

  + Code on Demand ( optional )

+ 장단점 

  + 장점
    + HTTP 프로토콜 인프라를 그대로 사용하므로 따로 구축할 필요가 없다
    + HTTP 프로토콜을 따르는 모든 플랫폼에서 사용이 가능한다
    + 의도하는 바를 명확하게 나타냄으로 쉽게 파악할 수 있다. 
  + 단점
    + 사용할 수 있는 메소드가 4가지 밖에 없다 (GET, POST, PUT, DELETE)
    + 표준 자체가 존재하지 않아 정의가 필요하다 
    + 구형 브라우저에서 호환이 되지 않는 경우가 있다



## RESTful

REST 아키텍처 원칙을 모두 만족하는 API





## RESTful API





> 참고
>
> + https://sanghaklee.tistory.com/57
