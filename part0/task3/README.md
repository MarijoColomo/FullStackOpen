```mermaid
sequenceDiagram
Participant user 
participant browser 
participant server

user ->>browser: writes a new note and click save
Note right of browser: Sending the note to server

browser ->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
activate server
Note right of server: note saved by the server
server ->>browser: {content: "learning", date: "2025-08-27T21:32:36.268Z"}
deactivate server

Note right of browser: server does not request a redirect, the browser remains on the same page
