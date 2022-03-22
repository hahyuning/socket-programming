# Socket Programming
- TCP는 연결지향형 서비스로 신뢰적 바이트 스트림 채널을 제공하는데, 이 채널을 통해 데이터가 두 종단 시스템 사이를 흐르게 된다.
- UDP는 비연결형이고 한 종단 시스템에서 다른 곳으로 데이터를 독립적인 패킷으로 만들어서 보내는데 전송에 대한 순서와 도착을 보장하지 않는다.
<br>

## 1. UDP 소켓 프로그래밍
- 송신 프로세스는 목적지 호스트 IP 주소와 목적지 소켓의 포트 번호로 구성된 목적지 주소를 패킷에 붙인다.
- 이 패킷이 송신자의 소켓을 통과한 후 인터넷은 이 목적지 주소를 이용하여 패킷을 수신 프로세스에 있는 소켓으로 라우트 한다.
- 패킷이 수신 소켓에 도착하면 수신 프로세스는 소켓을 통해 그 패킷을 추출하고 다음에 패킷의 콘텐츠를 조사하고 적절한 동작을 취한다.
- UDP 소켓 프로그래밍에서 클라이언트가 메시지를 전송하기 전에 서버가 프로세스를 수행하고 있어야 한다.
<br>

## 2. TCP 소켓 프로그래밍
- TCP 연결을 생성할 때 클라이언트 소켓 주소와 서버 소켓 주소를 연결시킨다.
- TCP 연결이 설정된 후 한쪽에서 다른 쪽으로 데이터를 보내려면 소켓을 통해 데이터를 TCP 연결로 보내면 된다.
   (UDP에서는 서버가 패킷을 소켓에 제공하기 전에 패킷에 목적지 주소를 붙임)
- 클라이언트는 서버로의 접속을 시도하는데, 서버는 클라이언트의 초기 접속에 응대할 수 있도록 준비하고 있어야 한다.
- UDP와 마찬가지로 TCP 서버는 클라이언트가 접속을 시도하기 전에 프로세스를 먼저 수행하고 있어야 한다.
- 서버 프로그램은 임의의 컴퓨터에서 수행되고 있는 클라이언트로부터 초기 접속을 처리하는 특별한 소켓을 가져야 한다.
- 서버 프로세스가 수행되면 클라이언트 프로세스는 서버로의 TCP 연결을 시도하고, 이는 클라이언트 프로그램에서 TCP 소켓을 생성함으로써 가능하다.
- 클라이언트는 TCP 소켓을 생성할 때 서버에 있는 환영 소켓의 주소, 즉 서버의 IP 주소와 소켓의 포트 번호를 명시한다.
- 소켓을 생성한 후 클라이언트는 세 방향 핸드셰이크를 하고 서버의 환영 소켓과 TCP 연결을 설정한다.
- 세 방향 핸드셰이크 동안 클라이언트 프로세스는 서버 프로세스의 출입문을 두드리고, 서버가 노크 소리를 들으면 서버는 새로운 출입문, 즉 해당 클라이언트에게 지정되는 새로운 연결 소켓을 생성하고 TCP 연결
- 애플리케이션 관점에서 볼 때 클라이언트의 소켓과 서버의 연결 소켓은 파이프에 의해 직접 연결된다.
- 클라이언트 프로세스는 자신의 소켓으로 임의의 바이트를 보낼 수 있으며 보낸 순서대로 서버 프로세스가 바이트를 수신하도록 TCP가 보장한다.
