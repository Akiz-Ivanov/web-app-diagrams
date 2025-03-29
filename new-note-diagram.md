```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note left of Browser: User fills form & clicks "Save"

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Note right of Server: Server appends note to data.json
    Server-->>Browser: 302 Redirect → https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Server
   
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

  
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server


    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server
    
    Note right of Browser:  the JavaScript code starts executing and fetches data

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: JSON data
    deactivate Server

    Note left of Browser: Displays updated notes
