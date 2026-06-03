flowchart TD
    User["👤 User\nwww.foobar.com"]

    subgraph LB_Cluster["⚖️ HAProxy Cluster"]
        LB1["HAProxy 1"]
        LB2["HAProxy 2"]
        LB1 <-->|"sync"| LB2
    end

    subgraph WebServer["🖥️ Web Server"]
        Nginx["🌍 Nginx\nServes static files\nHandles HTTP/HTTPS"]
    end

    subgraph AppServer["⚙️ Application Server"]
        App["🔧 App Server\nRuns business logic\nProcesses dynamic requests"]
        Code["📁 Code Base"]
        App --> Code
    end

    subgraph DBServer["🗄️ Database Server"]
        DB[("🟢 MySQL\nStores & manages data")]
    end

    User -->|"HTTPS"| LB_Cluster
    LB_Cluster --> WebServer
    WebServer --> AppServer
    AppServer --> DBServer
