```mermaid
sequenceDiagram
    participant browser
    participant server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    Note right of browser: The single HTML document is fetched from the server. Its content is manipulated by JavaScript that executes in the browser.
    Note right of browser: Unlike traditional web apps where each page is fetched separately, only the HTML page is fetched and its content is manipulated by JavaScript.
    activate browser
    browser-->>server:POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note left of server: when a user creates a new note that's the form input is being filled and 'save' button is pressed. The browser makes a POST request to this URL. And it contains the new note which is being typed  as JSON data
    activate server
    server-->>browser:The server responds with the status code 201 which means the new note is succesffully created
    Note right of browser: The Content-Type header of the request tells the server that the included data is represented in JSON format which enables the server to correctly parse data
    Note right of browser: Unlike the traditional web apps, this SPA version does not ask for a redirect. Rather the browser stays on the same page and no further HTTp request is sent. It uses the JS code which is already fetch from the server.  
