@startuml
skinparam BoxPadding 10
box "PC"
actor FileTransferChannel1
actor DataTransfer1
end box
box "PAD"
actor DataTransfer2
actor FileTransferChannel2
end box
[->FileTransferChannel1: CreateFileTransferChannel
activate FileTransferChannel1
FileTransferChannel1 -> DataTransfer1: Create Socket
deactivate FileTransferChannel1
activate DataTransfer1

]->FileTransferChannel2: CreateFileTransferChannel
activate FileTransferChannel2
FileTransferChannel2 -> DataTransfer2: Create Socket
deactivate FileTransferChannel2
activate DataTransfer2

]->FileTransferChannel2: ReceiveFile
activate FileTransferChannel2

[->FileTransferChannel1: SendFile
activate FileTransferChannel1
FileTransferChannel1 -> FileTransferChannel1: Retransmission processer thread
activate FileTransferChannel1
FileTransferChannel1 -> FileTransferChannel1: Zip File
activate FileTransferChannel1
deactivate FileTransferChannel1

loop
FileTransferChannel1 -> DataTransfer1: Push
DataTransfer1 -> DataTransfer2: Send
DataTransfer2 -> FileTransferChannel2: Receive Data
FileTransferChannel2 -> FileTransferChannel1: Retransmission Request
end loop

FileTransferChannel2 -> FileTransferChannel2: Unzip File
activate FileTransferChannel2
FileTransferChannel2 ->]: Return File Path
deactivate FileTransferChannel2
deactivate FileTransferChannel2
deactivate DataTransfer2

[-> FileTransferChannel1: CloseTransfer
deactivate FileTransferChannel1
deactivate FileTransferChannel1
deactivate DataTransfer1

@enduml