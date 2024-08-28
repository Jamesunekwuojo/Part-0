```mermaid
sequenceDiagram
    participant browser
    participant server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    Note right of browser: The single HTML document is fetched from the server. 
    Its content is being manipulated by the JavaScript that executes in the browser. 
    Unlike traditional web apps where each page is fetched separately, only the HTML page is fetched, and its content is manipulated by 
    JavaScript.

