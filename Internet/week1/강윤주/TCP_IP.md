# TCP/IP 

TCP/IP는 OSI 7Layers 중 Layer3, Layer4를 다루는 프로토콜이다.

인터넷 프로토콜 스위트(Internet Protocal suite)는 인터넷이 서로 통신할 때 쓰이는 통신규약의 모음이다.

이 중 TCP와 IP가 가장 많이 쓰이기 때문에 TCP/IP라고 부른다.

TCP는 전송 조절 프로토콜이고 IP는 패킷 통신 방식의 인터넷 프로토콜이다.

TCP/IP를 사용한다는 것은 IP주소체계를 따르고 IP 라우팅을 이용해 목적지에 도달하여 TCP의 특성을 활용해 송신자와 수신자의 논리적 연결을 생성하고 신뢰성을 유지할 수 있도록 하겠다는 것을 의미한다.

IP만 가지고는 목적지와 경로를 설정할 수 있지만 순서를 보장할 수 없다.

TCP로 순서를 보장하고 이외 데이터가 제대로 도달하는지 확인한다.

TCP는 IP 정보 외에도 port 정보를 이용해 연결한다. endpoint에 도달한 데이터가 어느 port로 들어가야 하는지 알아야 하기 때문이다.

TCP의 특징

- 흐름제어
- TCP Header 내의  Window size를 이용해 한번에 받고 보낼 수 있는 데이터 양을 정함. 여기서 window는 일정량의 데이터를 의미. 이는 3-way handshake에서 수신자가 정함.
- 자신이 지금까지 받은 데이터 양을 송신자에게 보냄. Acknowledgment Number
- 이 다음 몇번부터 보내면 될지 수신자에게 보냄. Sequence Number
- 혼잡제어
- 네트워크망의 혼잡
- Slow Start 데이터 송출량을 작게 시작해서 점점 키워 적합한 송출량을 찾음
