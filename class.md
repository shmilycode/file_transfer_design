@startuml

class RetransmissionClient{
  void RequestRetransmission()
  void OnRetransmission()
}

class RetransmissionServer{
  void Run()
}

class DataTransfer{
  void Write()
  void Read()
  void Close()
}

class MulticastTransfer{
  void JoinGroup()
}

class FileTransferServer{
  void SendFile()
}

class FileTransferClient{
  void ReceiveFile()
}

class FileHandler{
  void Handle()
}

class FileZip{
  void Zip()
  void UnZip()
}

DataTransfer <|- MulticastTransfer

FileTransferServer --> RetransmissionServer
FileTransferServer --> DataTransfer
FileTransferClient --> RetransmissionClient
FileTransferClient --> DataTransfer

FileHandler <|- FileZip 
@enduml