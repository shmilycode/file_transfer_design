@startuml

class SocketClient{
  void Read();
  void Write();
  void Connect();
  void Disconnect();
}

class SocketServerDelegate{
  void OnConnect(Socket);
  void OnDisconnect();
  void OnReceive();
}

class SocketBase{
}


SocketServer +---left SocketServerDelegate
SocketServer *-- SocketBase
SocketClient *-- SocketBase
SocketBase <|-- TCPSocket
SocketBase <|-- UDPSocket
@enduml