# 3 Ways Handshake

TCP가 연결을 시작하는 과정

TCP Header 내의 SYN, SYN/ACK, ACK Flag 이용

1. 송신자가 수신자에게 SYN을 보내 통신이 가능한지 확인한다. 이때 포트가 열려있어야 한다.
2. 수신자는 SYN을 받고 송신자에게 SYN/ACK를 보내 통신할 준비가 되었음을 알린다.
3. 송신자가 SYN/ACK를 받고 ACK를 보내 전송을 시작함을 알린다.