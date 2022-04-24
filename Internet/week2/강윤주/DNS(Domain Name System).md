# DNS(Domain Name System)

- IP주소를 도메인으로 바꾸거나 도메인을 다시 IP주소로 바꾸어주는 데이터베이스 시스템
- 연결되어있는 IP주소와 도메인이 저장된 곳이 DNS
- 각 도메인들마다 DNS와 연결해주는 서버 역할을 하는 DNS 서버, 다른 말로 네임서버가 있다.

## DNS 구성 요소

### 1. 도메인 네임 스페이스 (Domain Name Space)

– 데이터 이름 관련 규칙 정의

– 자원 레코드라는 정보 집합체로 표현

### 2. 네임 서버 (Name Server)

– 도메인 트리 정보 관리 프로그램

– 도메인 네임 질의에 응답 서비스

### 3. 해석기

– 네임서버로부터 도메인 네임 정보수집

– 네임 서버의 정보로 질의에 응답

### Recursive Query

![DNS](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f566f28b-6aa4-4c77-9468-ee2d8a643005/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220424%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220424T120210Z&X-Amz-Expires=86400&X-Amz-Signature=40c2936b77819735694b357156a7ca65a13675daec05121de6ebebc1bc69a521&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

PC가 도메인 이름으로 Local DNS에 질문 (정보 없음→)

Local DNS가 Root DNS에 물어봄(정보 없음→)

Local DNS가 com DNS에 물어봄(정보 없음→)

Local DNS가 naver.com에 물어봄(찾아서 전달)

### * 참고

- http://www.naver.com/index.html -> URL
- [www.naver.com](http://www.naver.com) -> Host Name
- .com -> Top-level Domain Name
- .naver.com -> Second-level Domain Name