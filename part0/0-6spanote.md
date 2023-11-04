sequenceDiagram
    title SPA New Note Diagram
    participant user
    participant browser
    participant server

    user->>browser: Input new note value and click save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: Payload content is the content entered in the text box
    server->>browser: Return {"message":"note created"} and status code
    deactivate server