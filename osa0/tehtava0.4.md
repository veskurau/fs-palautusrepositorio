# Tehtävä 0.4: uusi muistiinpano
![Tehtävä 0.4](tehtava0.4.png "uusi muistiinpano")

sequenceDiagram

    participant browser
    participant server
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of browser: The browser also sends the data in the form
    Note left of server: The server creates a note-object according to received data ands adds it to list
    server-->>browser: URL redirection to /exampleapp/notes
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "My First Note", "date": "2024-09-13" }, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 
