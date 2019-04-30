@startuml

participant PC
participant FileTransferServer
participant FileTransferClient
participant Pad

PC [#0000FF]-> Pad: <<TransferStartNotify>>
activate PC
activate Pad
Pad -> FileTransferClient: Wake Up
activate FileTransferClient 
Pad [#0000FF]--> PC: <<TransferStartResponse>>
deactivate Pad
PC -> FileTransferServer: Wake Up
deactivate PC
activate FileTransferServer

group transfer
    FileTransferServer -> FileTransferClient: Send 
    FileTransferServer -> FileTransferServer: HttpServer
    activate FileTransferServer
    FileTransferClient ->FileTransferServer: Retranmission Request
    deactivate FileTransferServer
end

FileTransferClient -> Pad: Finish
deactivate FileTransferClient 
Pad [#0000FF]-> PC: <<Complete>>

PC ->FileTransferServer: Quit
deactivate FileTransferServer

@enduml