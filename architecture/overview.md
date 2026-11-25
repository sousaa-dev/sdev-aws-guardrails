# Architecture review

```mermaid
flowchart TD
  U[Authorized users] --> I[Identity and roles]
  I --> A[Application layer]
  A --> D[Private data storage]
  A --> L[Protected audit records]
  D --> L
  L --> R[Audit review]
```

Logical model only. Requirements: individual identities, constrained permissions, encrypted storage and communication, protected evidence, recovery ownership and review. No network exposure or account provisioning is implied.
