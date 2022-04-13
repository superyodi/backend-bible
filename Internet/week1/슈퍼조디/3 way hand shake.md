# 3 Way Handshaking



TCP 프로토콜은 연결지향형 프로토콜이기 때문에 데이터를 전송하기 전에 수신측과 송신측이 서로 연결되는 작업이 필요*



![TCP 패킷, 세그먼트의 구조, TCP 플래그의 설명](https://t1.daumcdn.net/cfile/tistory/9948B8415C6F93100F)



### 3 Way Handshaking

+ 클라이언트와 서버 모두 데이터를 전송할 준비가 되었다는 것을 보장하고 실제 데이터 전달이 시작되기 전에 다른 한쪽이 준비가 되었다는 것을 알 수 있도록 한다. 
+ 컨트롤 비트
  +  3 way handshaking이 수행되기 위해서는 TCP 헤더에 표시한 플래그들이 사용되는데 이러한 플래그들을 컨트롤 비트라고 부른다. 



그 중 **ACK, SYN ** 플래그가 사용된다. 

  

![img](https://t1.daumcdn.net/cfile/tistory/225A964D52F1BB6917)



+ SYN
  + 데이터 연결 할거임

### 4 Way Handshaking

![img](https://blog.kakaocdn.net/dn/qUXSw/btqDWsFNWJw/hVdKIneSYb7UK3wc0pj6Z0/img.png)
