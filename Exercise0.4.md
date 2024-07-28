```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST request to https://studies.cs.helsinki.fi/exampleapp/new_note  when form button is clicked
    Note right of browser: The browase makes a POST request to the URL when the 'save buuton' of the form element is clicked
    activate server
    server-->>browser: responds with status code 302 which is a URL redirect
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    Note right of browser: Due to this the browser reloads the note page causing three(3) more HTTP requests. fetching main.css, main.js and the raw data of notes 'data.json'

    activate server
    server-->>browser: Note page
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: main.css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: main.js file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Raw json data
    Note left of server: This json data is modified version with the data entered  when creating the new note. However all this changes will disappear whenever the server is being restarted  because all this is only on the server and is not stored in the database.
    deactivate server



