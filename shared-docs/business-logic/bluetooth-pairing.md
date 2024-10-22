# Bluetooth Pairing Process

The following sequence diagram illustrates the Bluetooth pairing process:


```mermaid
sequenceDiagram
    participant U as User
    participant A as App
    participant D as Device

    U->>A: Initiate pairing
    activate A
    A->>A: Enable Bluetooth
    Note right of A: Bluetooth initialization
    
    A->>D: Discover nearby devices
    activate D
    D-->>A: Send device info
    deactivate D
    A->>U: Display available devices
    
    U->>A: Select device
    A->>D: Send pairing request
    activate D
    Note right of D: Pairing process start
    
    D->>D: Generate pairing code
    D-->>U: Display pairing code
    
    U->>A: Enter pairing code
    A->>D: Send pairing code
    
    D->>D: Verify pairing code
    Note right of D: Verification process
    D-->>A: Confirm pairing
    deactivate D
    
    A->>U: Display success message
    deactivate A