# OAuth



## 1. 사용 상황

외부앱에서 소셜 로그인을 사용해서 외부 소셜 계정의 정보를 가져와 사용할 수 있다. 
이때 사용되는 프로토콜이 OAuth

**OAuth 정의**

> OAuth는 인터넷 사용자들이 비밀번호를 제공하지 않고 다른 웹사이트 상의 자신의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 공통적인 수단으로서 사용되는,
> <u>접근 위임을 위한 개방형 표준</u>






## 2. OAuth 참여자

OAuth 동작에 관여하는 참여자는 크게 세가지로 구분할 수 있다. 
+ Resource Server: Client가 제어하고자 하는 자원을 보유하고 있는 서버
  + Facebook, Google, KakaoTalk 등이 이에 속한다.
+ Resource Owner: 자원의 소유자
  + Client가 제공하는 서비스를 통해 로그인 하는 **실제 유저**가 이에 속한다. 
+ Client: Resource Server에 접속해서 정보를 가져오고자 하는 클라이언트(웹 어플리케이션)




## 3. OAuth Flow

간단한 웹 어플리케이션 제작을 통해 OAuth의 동작 프로세스를 이해해 보기 

 **Client 등록**

**Resource Owner의 승인**

**Resource Server의 승인**

 **API 호출**

**Refresh Token**



> 자료 출처
>
> + https://tecoble.techcourse.co.kr/post/2021-07-10-understanding-oauth/

---

