---
config:
  layout: elk
---
flowchart TD
    User([User])
    Agent["Google ADK Agent"]
    Draft["Generate Email Draft"]
    Confirm{"User Confirmation"}
    Tool["send_email()"]
    Token[("token.json")]
    OAuth["Google OAuth"]
    Service["Gmail Service"]
    Email["Create EmailMessage"]
    Encode["Base64 Encode"]
    API["Gmail API"]
    Success["Success / Error"]

    User --> Agent
    Agent --> Draft
    Draft --> Confirm
    Confirm -->|Edit| Draft
    Confirm -->|Send| Tool
    Tool --> Token
    Token -->|Valid| Service
    Token -->|Invalid| OAuth
    OAuth --> Service
    Service --> Email
    Email --> Encode
    Encode --> API
    API --> Success
    Success --> User

    classDef user stroke:#818cf8,fill:#eef2ff,color:#1e1b4b;
    classDef agent stroke:#a78bfa,fill:#f5f3ff,color:#3b0764;
    classDef action stroke:#2dd4bf,fill:#f0fdfa,color:#134e4a;
    classDef decision stroke:#facc15,fill:#fefce8,color:#713f12;
    classDef auth stroke:#fb923c,fill:#fff7ed,color:#7c2d12;
    classDef api stroke:#38bdf8,fill:#f0f9ff,color:#0c4a6e;
    classDef result stroke:#4ade80,fill:#f0fdf4,color:#14532d;

    class User user;
    class Agent agent;
    class Draft,Tool,Email,Encode action;
    class Confirm decision;
    class Token,OAuth,Service auth;
    class API api;
    class Success result;
