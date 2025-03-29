```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note left of Browser: User submits form (JS prevents reload)
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate Server
    Note right of Server: Validates and adds new note to the data.json
    Server-->>Browser: 201 Created (Confirmation)
    deactivate Server
    Note left of Browser: JS updates DOM with new note
