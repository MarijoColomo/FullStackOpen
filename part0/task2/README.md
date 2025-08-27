# Task 2 
```mermaid
sequenceDiagram
Participant user 
participant browser 
participant server 
    
user ->>browser: access to the page
browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
activate server
server ->>browser: HTML document
deactivate server

browser ->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server ->>browser: the css file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
activate server
server-->>browser: the JavaScript file
deactivate server

browser->>server:  GET /local-storage.js 
activate server 
server-->>browser: local-storage.js 
deactivate server 

browser->>server:  GET /fte-utils.js 
activate server 
server-->>browser: fte-utils.js 
deactivate server 

browser->>server:  GET /express-fte.js 
activate server 
server-->>browser: express-fte.js 
deactivate server 

browser->>server:  GET /express-utils.js 
activate server 
server-->>browser: express-utils.js 
deactivate server 

browser->>server:  GET https://studies.cs.helsinki.fi/exampleapp/data.json 
activate server 
server-->>browser: [{"content":"","date":"2025-08-27T09:50:45.514Z"}, ... ]
Note right of server: The JSON document 
deactivate server 

Note right of browser: The SPA's Javascript starts running thanks to the browser
Note right of browser: The browser executes the callback function that renders the page
