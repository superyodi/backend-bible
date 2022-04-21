# OSI 7 Layer

* 상위 계층은 Programmer가 구현하는 부분, 전송서비스는 OS에 포함되어 있음.
* Data를 보내고자 한다면:
  * 4계층에서 Data를 자른다.(각 Number 부여, 이를 통해 잘 전송 되는지 확인) → Segment
  * 3계층에서  Segment에 IP(자신의 IP, 목적지의 IP)를 부여한다. → Packet
  * 2계층에서 신뢰성 있는 통신을 책임진다. → Frame
  * 1계층에서는 전송한다.
    * 1계층은 Data를 주고받는 매체에 대한 것이다. (Ex: 동축, LAN...etc)

* 내부 Network는 2계층까지만 되면 된다.

### 용어

* **Switch** : 여러개의 연결을 모아서 하나로 보내준다.
* **Gateway** : Switch의 Switch, 외부로 연결되어 있다.
* **Router** : 여러 개의 Input, 나가는 것도 여러개.
  * 나가는 것들 중 하나를 선택해야 한다. IP를 찾아 어디로 가야 하는지 안내해 주는 역할을 한다.
  * Router과 Switch를 구분 안하는 경우가 있다. Switch가 Router에 포함된다.

### 계층

* 2계층(Data Link Layer) : 각 Node 간의 통신을 보장한다. 여기서 보장하는 것은 End to End 말고 인접한 Node 간의 통신을 보장한다는 것이다.
  * Physical Layer에서 아무리 Data 전송 방법을 제공하더라도 불안정하므로 이것을 Cover하기 위해서(신뢰성 보장) 이 계층에서 구현한다.
  * 2계층의 기능은 두 개로 나뉜다.
    * Error Correction : Data가 잘 왔는지 확인하고, 잘 오지 않았으면 재 전송을 요청한다.
    * MAC(Multiple Access Control) : 두 곳에서 동시에 전송할 때 같은 매체를 쓴다면 Data 간섭이 일어나서 엉뚱한 Data가 올 수 있으므로 순차적으로 보내기 위해 Control을 해준다.
* 3계층(Network Layer) : Gateway를 나와 목적지까지 갈 때 어떤 경로로 갈 지 결정해야 한다.
* **4계층(Transport Layer)** : End-to-End 간에 Data가 잘 도착하도록 보장해 주어야 한다.
  * 하위 계층에서 다 완벽하게 보장했더라도 Data가 잘 오지 않는 경우가 있음. 예를 들어 Router 중 하나가 과부화되어 Data를 버리면 다시 보내줘야 하는데 그러지 못한 상황이 있을 수 있다. 다른 경우는 Router 간 Loop를 돌거나. 