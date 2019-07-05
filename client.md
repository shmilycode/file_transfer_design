@startuml

class RetransmissionClient{
  void RequestRetransmission()
}

class TransferServer{
  void WriteSlice()
  void ReadSlice()
}


class UnreliableFileTransferClient{
  void ReceiveFile()
}

UnreliableFileTransferClient *-- RetransmissionClient
UnreliableFileTransferClient *-- TransferServer 
ReliableFileTransferClient *-- TransferClient
RetransmissionClient <|-- UDPRetransmissionClient
TransferServer --> SocketClient 
SocketClient <|-- SimpleNetClient
TransferClient --> SocketClient
@enduml