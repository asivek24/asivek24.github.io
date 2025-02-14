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

 1. An attacker installs malware on a large network of devices, enabling the attacker  
 to control the devices remotely and create botnets.  
 2. The attacker directs the botnet to flood the targeted web server with a large  
 amount of traffic.  
 3. The requests reach the firewall, which forwards the requests through to the web server  
 at first.  
 4. The web server sends responses back to the botnet until it becomes overloaded.  
 5. A request comes in from a client.  
 6. The request hits the firewall, which forwards it to the web server.  
 7. The web server is overloaded, so an error response/timeout message is returned to the client.  
 8. The firewall begins to analyze and filter incoming traffic.  
    * The firewall is triggered through rate limiting: when there is an excessive number of  
      requests per pre-determined period of time from IP addresses, it begins to block them.
 9. The botnet continues to send excessive requests, which hit the firewall.  
 10. The firewall recognizes the botnet as malicious and blocks the IP addresses.  
 11. The client tries to send another request, which reaches the firewall.  
 12. The firewall allows the request to pass through to the web server.  
 13. The web server is no longer overloaded, so a response is generated and  
 sent to the client.  






