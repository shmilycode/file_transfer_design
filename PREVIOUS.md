@startuml
participant PC 
participant RouteServer
participant Pad

[-> PC: Pull ENVX
PC -> RouteServer: Post ENVX
activate PC
activate RouteServer
RouteServer -> RouteServer: Parse ENVX
activate RouteServer
deactivate RouteServer
RouteServer --> PC: URL
deactivate RouteServer
PC -> Pad: URL
deactivate PC
activate Pad
Pad -> RouteServer: Http Request
activate RouteServer
RouteServer -> Pad: ENVX
deactivate RouteServer

@enduml