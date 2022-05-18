# Authentication & Authorization

> Authentication(인증)은 자신이 누구라고 주장하는 요청을 받아 동일인인지 확인하는 절차이다.

> Authorization(인가)는 자신이 누구인지 확인받은 이후 그 사람이 가진 권한에 알맞는 작업을 하는지 확인하는 과정이다.

## Basic Authentication

> 요청을 보낼 때 HTTP Header의 Authorization 헤더에 자신의 정보(예 : 유저 이름과 암호)를 인코딩(Base64) 후 넣어 같이 보내 인증 및 인가를 하는 방법

### 단점
* 결과적으로 인터넷에 자신의 비밀번호를 넣어서 보내는 것이기 때문에 만약 요청을 다른 누군가가 낚아챌 수 있다면 암호가 노출된다.
    * Base64 인코딩은 쉽게 복구가 가능하다.

## Token Authentication

> Client가 자신이 누구인지 Server측에서 알게 하고 자신만의 고유 정보가 담긴 Access Token을 받을 수 있는 Protocol이다.

### 장점
* Stateless하며 확장성이 있다.
    * 확장성의 반례: Session
* 보안성
    * 쿠키를 전달 할 필요가 없으므로 쿠키를 통해 발생하는 취약점이 사라진다.

### 단점
* Stateless하기 때문에 제어 불가능하다.
* Token 정보가 탈취되어도 무효화 불가능하다.
    * Stateless하기 때문에 탈취된 Token을 무효화할 수 없음.

### 단점 해결 방안
* Refresh Token을 두어 Access Token의 유효기간을 짧게 하여 탈취되어도 오래 쓰지 못하게 한다.

## JWT

> JSON Web Token의 줄임말로 JWT는 크게 Header, Payload, Signature로 구분된다.
* Header : Token Type, Hashing Algorithm...
* Payload : Web에서 활용하는 내용물
* Signature : 데이터 무결성과 변조 방지를 위한 서명. 서버만이 알고 있다.

### JWT 단점
* Signature 키를 보통 하나만 두는데 만약 털리면 답이 없다.
* 토큰 자체에 정보를 저장하므로 털릴 위험이 있다.

