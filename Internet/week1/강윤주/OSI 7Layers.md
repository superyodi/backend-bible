# OSI 7Layers

**OSI 모형** : (Open Systems Interconnection Reference Model)은 [국제표준화기구](https://ko.wikipedia.org/wiki/국제표준화기구)(ISO)에서 개발한 모델로,

컴퓨터 네트워크 프로토콜 디자인과 통신을 계층으로 나누어 설명한 것

- 프로토콜
  - **프로토콜**은 컴퓨터 내부에서, 또는 컴퓨터 사이에서 데이터의 교환 방식을 정의하는 규칙 체계입니다. 기기 간 통신은 교환되는 데이터의 형식에 대해 상호 합의를 요구합니다. 이런 형식을 정의하는 규칙의 집합을 프로토콜이라고 합니다.
  - [HTTP](https://ko.wikipedia.org/wiki/HTTP) : Hyper Text Transfer Protocol
  - [HTTPS](https://ko.wikipedia.org/wiki/HTTPS) : Hyper Text Transfer Protocol Secure
  - [FTP](https://ko.wikipedia.org/wiki/파일_전송_프로토콜) : File Transfer Protocol
  - [SFTP](https://ko.wikipedia.org/wiki/SSH_파일_전송_프로토콜) : Secure File Transfer Protocol
  - [Telnet](https://ko.wikipedia.org/wiki/텔넷) : TErminaL NETwork
  - [POP3](https://ko.wikipedia.org/wiki/POP3) : Post Office Protocol version 3
  - [SMTP](https://ko.wikipedia.org/wiki/SMTP) : Simple Mail Transfer Protocol
  - [SSH](https://ko.wikipedia.org/wiki/시큐어_셸) : Secure Shell
  - [SSL](https://ko.wikipedia.org/wiki/SSL) : Secure Socket Layer
  - [SOAP](https://ko.wikipedia.org/wiki/SOAP) : Simple Object Access Protocol
  - [ARP](https://ko.wikipedia.org/wiki/ARP) : Adress Resolution Protocol

> **OSI 7계층이란, 통신 접속에서 완료까지의 과정을 7단계로 정의한 국제 통신 표준 규약**

1. 물리

    : 전송하는데 필요한 기능을 제공 ( 통신 케이블, 허브 )

   - 컴퓨터가 통신할 때 0과1로 구성된 데이터를 아날로그 신호로, 또는 반대로 인코딩/디코딩해주는 하드웨어 모듈

2. 데이터링크

    : 송/수신 확인. MAC 주소를 가지고 통신함 ( 브릿지, 스위치 )

   - 같은 네트워크에 있는 여러대의 컴퓨터가 통신하기 위해 필요한 하드웨어 모듈
   - Framing : 여러 데이터를 전송 받을 경우 구분하기 위해 데이터 앞뒤에 특정 데이터(0000,1111,,,,)를 붙이는 작업
   - switch : 여러 대의 컴퓨터를 한 전선으로 연결했을 때 데이터의 목적지를 특정화하는 장치
   - router : 여러 스위치 또는 라우터를 연결해주는 장치

3. 네트워크

    : 패킷(데이터+IP주소)을 네트워크 간의 IP를 통해 데이터 전달 ( 라우팅 )

   - 여러 네트워크가 연결되어 있을 때 데이터의 목적지를 찾는 역할
   - 운영체제의 커널에 소프트웨어적으로 구현되어 있음

4. 전송

    : 두 host 시스템으로부터 발생하는 데이터 흐름 제공

   - 포트번호를 사용하여 데이터가 최종 목적지인 프로세스에 도달하게 해줌
   - 운영체제의 커널에 소프트웨어적으로 구현되어 있음

5. **세션** : 통신 시스템 사용자간의 연결을 유지 및 설정함

6. **표현** : 세션 계층 간의 주고받는 인터페이스를 일관성있게 제공

7. **응용** : 사용자가 네트워크에 접근할 수 있도록 서비스 제공

   

# 관련 질문

- **라우터와 스위치의 차이는?**

라우터는 3계층 장비로, 수신한 패킷의 정보를 보고 경로를 설정해 패킷을 전송하는 역할을 수행하는 장비

스위치는 주로 내부 네트워크에 위치하며 MAC 주소 테이블을 이용해 해당 프레임을 전송하는 2계층 장비

- **패킷이란**?