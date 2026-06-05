```mermaid
graph TD
    User((User)) --> LB1[HAProxy LB 1]
    User --> LB2[HAProxy LB 2]
    
    subgraph Load_Balancer_Cluster
    LB1 <--> LB2
    end
    
    LB1 --> Web1[Web Server 1]
    LB1 --> Web2[Web Server 2]
    LB2 --> Web1
    LB2 --> Web2
    
    subgraph Web_Tier
    Web1
    Web2
    end
    
    Web1 --> App1[App Server 1]
    Web1 --> App2[App Server 2]
    Web2 --> App1
    Web2 --> App2
    
    subgraph Application_Tier
    App1
    App2
    end
    
    App1 --> DB[(MySQL Database)]
    App2 --> DB
    
    subgraph Database_Tier
    DB
    end
