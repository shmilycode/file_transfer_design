@startuml

class RetransmissionClient{
  void RequestRetransmission()
  void OnRetransmission()
}

class RetransmissionServer{
  void AllocateAndRun()
}

class FileSender{
  void Write()
}

class FileReceiver{
  void AllocateAndRun()
}

class FileTransferServer{
  void SendFile()
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

FileTransferServer --> RetransmissionServer
FileTransferServer --> FileSender
FileSender <|-- MulticastFileSender
RetransmissionServer <-+ RetransmissionServerHandler
RetransmissionServer --> RetransmissionServerDelegate
RetransmissionServerDelegate <|-- RetransmissionServerDelegateImpl
RetransmissionServerDelegateImpl --> UDPRetransmissionServer
@enduml