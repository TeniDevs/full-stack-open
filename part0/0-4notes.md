sequenceDiagram
    title Notes Diagram
    participant browser
    participant server
    
    user->>browser: Input new note value and click save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of browser: Payload content is the content entered in the text box
    Note right of browser: Page is reloaded

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Returns the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: Returns the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Returns content of data.json: [{"content": "Lessgoooo","date": "2023-11-02T21:13:16.644Z"...
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes