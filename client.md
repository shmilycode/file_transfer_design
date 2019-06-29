@startuml

class RetransmissionClient{
  void RequestRetransmission()
  void OnRetransmission()
}

class FileReceiver{
  void AllocateAndRun()
}


class FileTransferClient{
  void ReceiveFile()
}

RetransmissionClient <|-- UDPRetransmissionClient
FileTransferClient --> RetransmissionClient
FileTransferClient --> FileReceiver
FileReceiver <-+ FileReceiverHandler
FileReceiver <|-- MulticastReceiver
MulticastReceiver --> UDPMulticastServer
@enduml