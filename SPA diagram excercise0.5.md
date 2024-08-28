```mermaid
sequenceDiagram
    participant browser
    participant server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    Note right of browser: The single HTML document fetch from the server, it's content is being manipulated by the Javascript that 
    executes in the  browser. Unlike the traditional web apps in which each page is being fetched seprately, here only the HTML page is 
    being fetched, and it's content is being manipulated by JavaScript.
    
