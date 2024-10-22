# User Sign In Process

The following sequence diagram illustrates the user sign-in process:

```mermaid
sequenceDiagram
    participant U as India User
    participant A as App
    participant S as Server
    participant V as Verification Service

    U->>A: Initiate claim ownership
    activate A
    Note right of A: Start verification process
    
    A->>S: Send claim request
    activate S
    
    S->>V: Request user verification
    activate V
    Note right of V: Generate verification code
    
    V-->>U: Send verification code
    Note right of U: Via SMS/Email
    
    U->>A: Enter verification code
    A->>S: Submit verification code
    
    S->>V: Verify code
    Note right of V: Validate code
    V-->>S: Confirm verification
    deactivate V
    
    S-->>A: Confirm ownership claim
    deactivate S
    
    A->>U: Display success message
    Note right of A: Process complete
    deactivate A