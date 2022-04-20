# TCP

## Multiplexing and Demultiplexing

### Multiplexing/demultiplexing

* **Socket을 구분하는 것은 Port이다.**
* 송신 시 자신의 Port와 Target의 Port를 적고, Error 검출 Code(Checksum 기반, 100% 검출 불가)를 Header에 넣어 아래로 내려보낸다.
* 수신 시 Segment의 Header를 봐서 Source Port와 Target Port를 통해 어떤 Socket을 통해 보냈는지 알 수 있다.

### How demultiplexing works

* Source Port #와 Dest Port #는 각각 16Bit이다.
* Other Header Fields는 TCP/UDP 종류에 따라 크기가 달라진다.
  * Checksum이 들어있다.
    * UDP도 오류가 발생하면 버려야 하기 때문에 Checksum이 필요하다.
  * TCP가 신뢰성 때문에 더 크다.

## Connectionless transport: UDP

### UDP: User Datagram Protocol

* 부가기능이 없고 뼈대만 있다.
  * Mux & Demux를 제공한다.
  * Error Check를 제공한다. (Best Effort)
* 동영상과 음악같은 Streaming Multimedia에 사용된다. 그리고 DNS나 SNMP의 Control Packet에도 사용된다.

#### 왜 쓰는가?

* 연결을 위한 작업을 아무것도 하지 않는다. 연결을 위한 작업은 Delay를 발생시킨다 → UDP는 그걸 하지 않으므로 빠르다.
* 송신자, 수신자에 대해 아무런 Connection State를 가지지 않으므로 단순하다.
* Header Size가 작다(Data 작고 빠르다)
* Congestion Control이 없다 - TCP에서는 Buffer가 모자라다면 Control 해서 천천히 보내는데 UDP는 원하는 만큼 빠르게 보낸다. 그렇기 때문에 Overhead가 크다.