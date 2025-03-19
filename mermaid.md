```mermaid
sequenceDiagram
    participant User
    participant n8n
    participant Agent
    participant ExternalAPI

    User->>n8n: Trigger Workflow
    n8n->>Agent: Execute Workflow
    Agent->>ExternalAPI: Make Request
    ExternalAPI-->>Agent: Receive Response
    Agent->>Agent: Process Data
    Agent-->>n8n: Return Processed Data
    n8n->>n8n: Format Output
    n8n-->>User: Deliver Final Response
```
