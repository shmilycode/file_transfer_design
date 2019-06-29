@startuml

class RetransmissionServer{
  void AllocateAndRun()
}

class FileSender{
  void Write()
}

class FileTransferServer{
  void SendFile()
}

FileTransferServer --> RetransmissionServer
FileTransferServer --> FileSender
FileSender <|-- MulticastFileSender
RetransmissionServer <-+ RetransmissionServerHandler
RetransmissionServer --> RetransmissionServerDelegate
RetransmissionServerDelegate <|-- RetransmissionServerDelegateImpl
RetransmissionServerDelegateImpl --> UDPRetransmissionServer
@enduml