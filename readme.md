## Flow Chart
---
title: Client App
---

```mermaid
flowchart TD

    subgraph LoginForm
        id0[DB Intitialization];
        id1[Login details] -- Connecting with Server --> id2[Server details];
        id33[Load ClientAPP]
    end
    
    subgraph speicherDetails
        direction LR
        id3[Speicher details] --> id4[Server details];
    end
    
    subgraph version
        direction LR
        id5[Master Version] --> id6[Server details] --> id7[Gateway Version details/];
    end
    
    subgraph updateType
        direction LR
        id8[Autotest] --> id9[Customer Program];
    end
    
    subgraph type
        id10[Gateway] --> id9[Customer Program];
        id10[Gateway] --> id8[Autotest];
        id11[Master] --> id9[Customer Program];
        id11[Master] --> id8[Autotest];
    end
    
    subgraph client
        id15[Initializing Client Class];
        id16[Binding UDP client to local port];
        id17[Server Connection];
    end
    
    subgraph formLoad
        id18[Remote IP Endpoint creation];
        id19[Login Form loading];
        id20[User role identification];
        id21[Sending User Data to Server];
    end
    
    subgraph formDesign
        id12[Component Intitialization];
        id13[Setting defaults for Radio-Buttons];
        id14[Assigning Behaviors for Buutons];
        formLoad
    end
    subgraph speicherUpdater
        version;
        speicherDetails;
        client;
    end
    subgraph clientAppForm
        direction TB
        updateType;
        formDesign;
        speicherUpdater;
    end
    subgraph fieldsCheck
        direction TB
        id12253[Not Null] --> |Gateway Version/Master Version/Slave Version/Update Type|id22553{Check?};
        id22553{Check?} --> |Failed| id12256523[Throws Exception]
        id22553{Check?} --> |Passed| id122652656[Mouse Event Handling]
    end
    
    subgraph speicher
        id1223[Speicher Intitialization];
        fieldsCheck
        id22222[Gateway Version];
    end
    
    
    id100([Start ClientApp]) --> Program;
    Program --> LoginForm;
    LoginForm --> formDesign;
    LoginForm --> Login;
    formLoad --> id33[Load ClientAPP];
    Assembly --> clientAppForm;
    Version --> Assembly;
    Login --> id223((Login Message))
    id223{Success?} --> |Yes| clientAppForm;
    id223{Success?} --> |Else| id224((.))
    id224((.)) --> |NOLOGIN| id225[Send Username] --> id226[Server];
    id224((.)) --> |ERROR| id227[Show Error];
    id224((.)) --> |INFO| id228[Display Information];
    id226[Server] --> speicherUpdater;
    speicherUpdater --> Update;
    Update --> speicher
    speicher --> id200([Close ClientApp]) 
    
    style id100 fill:#1ed760,stroke:#333,stroke-width:4px
    style id200 fill:#cc0000,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
    
```
    
