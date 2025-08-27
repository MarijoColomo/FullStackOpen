# Task 1 
```mermaid
sequenceDiagram
Participant user 
participant browser 
participant server 
    
user ->>browser: writes a new note and click save 
Note right of browser: Sending the note to server 
browser->>server:  POST https://studies.cs.helsinki.fi/exampleapp/new_note 
Note right of server: note in server is already save 
server-->>browser:  302 Found and redirected 

browser->>server:  GET https://studies.cs.helsinki.fi/exampleapp/notes 
activate server 
server-->>browser: HTML document 
deactivate server 

Note right of browser: browser request the resources again (css, js) 
browser->>server:  GET https://studies.cs.helsinki.fi/exampleapp/main.css 
activate server 
server-->>browser: the css file 
deactivate server 

browser->>server:  GET https://studies.cs.helsinki.fi/exampleapp/main.js 
activate server 
server-->>browser: the javascript file 
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
server-->>browser: JSON "Probando” 
Note right of server: The JSON document now contains the new note 
deactivate server 

Note right of browser: The browser executes the JS that renders the notes 
