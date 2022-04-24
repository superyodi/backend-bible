# HTTP(HyperText Transfer Protocol)

: 텍스트 기반의 통신 규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜

클라이언트가 브라우저를 통해 서비스를 요청하면 서버에서 해당 요청의 결과를 찾아 응답한다.

- HTTP메시지는 HTTP서버와 HTTP클라이언트에 의해 해석된다.
- TCP/IP를 이용하는 응용 프로토콜이다.
- 연결상태를 유지하지 않는 비연결성 프로토콜이다.

(이러한 단점을 해결하기 위해 Cookie와 Session이 등장)

- 연결을 유지하지 않는 프로토콜이기 때문에 요청/응답 방식으로 동작한다.

## 요청

### Request Method

- GET : 요청
- POST : 생성
- PUT : 수정
- DELETE : 삭제

### 예시

```
GET <https://velog.io/@surim014> HTTP/1.1								// 시작줄
//1. Method 주소 버전
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...			  // 헤더
Upgrade-Insecure-Requests: 1

//2. 요청에 대한 정보
//3. 데이터
```

## 응답

### Status Code

- **1XX (조건부 응답)** : 요청을 받았으며 작업을 계속한다.
- **2XX (성공)** : 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며 성공적으로 처리했음을 가리킨다.
- **3XX (리다이렉션 완료)** : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
- **4XX (요청 오류)** : 클라이언트에 오류가 있음을 나타낸다.
- **5XX (서버 오류)** : 서버가 유효한 요청을 명백하게 수행하지 못했음을 나타낸다.

### 예시

```
HTTP/1.1 200 OK														// 시작줄
//1. 버전 상태코드 상태 메시지
Connection: keep-alive												 // 헤더
Content-Encoding: gzip
Content-Length: 35653
Content-Type: text/html;
//2. 응답에 대한 정보
<!DOCTYPE html><html lang="ko" data-reactroot=""><head><title...
3. 본문
```

## 사용예시