```mermaid
graph TD
    User((User)) --> LB[Load Balancer]
    LB --> WS1[Web Server 1]
    LB --> WS2[Web Server 2]
    LB --> WS3[Web Server 3]
    WS1 --> App[Application Server]
    WS2 --> App
    WS3 --> App
    App --> DB[MySQL Database]
    
    subgraph Monitoring
    M[Monitoring Client]
    end
    WS1 -.-> M
    WS2 -.-> M
    WS3 -.-> M
