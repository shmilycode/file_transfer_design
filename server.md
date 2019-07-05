@startuml

class RetransmissionServer{
  void AllocateAndRun()
  void OnRetransmissionRequest()
}

class TransferServer{
}

class UnreliableFileTransferServer{
  void SendFile()
}

class TFileTransferServer {
  void SendFile()
}

UnreliableFileTransferServer *-- RetransmissionServer
TFileTransferServer ---> TransferServer
UnreliableFileTransferServer *-- TransferClient 
TransferClient --> SocketClient 
TransferServer --> SocketServer
SocketServer <|-- SimpleSocketServer
RetransmissionServer <-+ RetransmissionServerHandler
RetransmissionServer <|-- UDPRetransmissionServer
UDPRetransmissionServer --> SocketServer
SocketClient <|-- SimpleSocketClient
@enduml