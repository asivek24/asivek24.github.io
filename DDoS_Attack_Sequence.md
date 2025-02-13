## Sequence of DDoS Attack

```mermaid
sequenceDiagram
actor Attacker
participant BotNet
actor Client
participant Firewall
participant WebServer
 Attacker->>BotNet: Attack Target WebServer
 BotNet->>+Firewall: Send Excessive Requests
 Firewall->>+WebServer: Forward Requests
 WebServer-->>-BotNet: Send Response
 Client->>Firewall: Send Request
 Firewall->>+WebServer: Forward Requests
 note right of WebServer: Server is Overloaded
 WebServer-->>-Client: Error Response/Timeout
 Firewall->>Firewall: Analyze Traffic
 BotNet->>+Firewall: Send Excessive Requests
 Firewall-->>-BotNet: Block IP Address
 Client->>Firewall: Retry Request
 Firewall->>+WebServer: Forward Requests
 WebServer-->>-Client: Send Response
 ``` 
