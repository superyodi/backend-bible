# 3-Way Handshaking & 4-Way handshaking

## connection management

Data를 주고 받기 전에 송신자와 수신자는 handshake를 한다.

* 송신자는 수신자에게 특정 번호로 시작한다 알려준다.
* 수신자는 송신자에게 Receiver Buffer 크기를 알려준다.
* Client-to-Server의 시작 번호는 Random이다(0부터 시작하는거 아님)

### TCP 3-way handshake

* 송신자의 TCP Header에서 SYN Bit 1로 설정하여 연결 해도 되나 물어본다.
  * 임의의 Sequence Number를 보낸다.
* 수신자는 요청을 받으면 자신의 Sequence #을 보낸다.
  * 이 때 SYN Bit는 연결을 허용한다는 의미에서 1로 설정한다.
  * 이 때 ACK Bit는 잘 받았다는 의미에서 1로 설정한다.
  * 이 때 ACK Num은 받은 Sequence Number에 1을 더한 값을 보낸다 - 이 값으로 보내라는 의미
  * 이 때 Sequence Number를 수신자에서 임의로 설정하여 보낸다.
* SYN, ACK를 받은 송신자는 통신이 가능하다고 판단하여 ACK을 보낸다.
  * 이 때 ACK bit를 잘 받았다는 의미로 1로 설정한다.
  * 이 때 ACKnum은 수신자가 받은 Sequence #에서 1을 더한 값을 보낸다.

### TCP: closing a connection

* Client가 Socket을 닫는다.
  * 이 때 FIN bit를 1로 설정한다.
  * 이 때 seq를 x로 설정한다.
* Server에서 끝내고 싶은지 확인한다.
  * 이 때 ACK bit를 1로 설정한다.
  * 이 때 ACK Number를 x + 1로 설정한다.
  * 이때까지는 Data를 보낼 수 있다.
* Server에서 close하려고 보낸다.
  * 이 때 FIN bit를 1로 설정한다.
  * 이 때 Server의 Sequence #을 보낸다.
* Client에서 확인 ACK을 보낸다.
  * 보내기 전에 Segment의 유효기간의 두배를 기다린다. 만약 Data 쭉 보냈어도 ACK 보낸 다음 Timer동안 기다리지 않는다면 Server는 Close가 불가하다.
  * 만약 잘 왔다면 ACKbit를 1로 하고, ACKnum을 Server의 Sequence Number + 1로 하여 연결을 종료한다.
