
# 0.4: New note diagram

``` mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: new HTTP GET to location /notes
    deactivate server

    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: Code HTML
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the main.css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the main.js JavaScript file
    deactivate server

    Note over browser,server: The browser starts executing the JavaScript <br/>code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note over browser,server: The browser executes the callback function that <br/> renders the notes
```


# 0.5: Single page application diagram

``` mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: Code HTML
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the main.css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the spa.js JavaScript file
    deactivate server

    Note over browser,server: The browser starts executing the JavaScript <br/>code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "hola buenas tardes", "date": "2024-03-27T17:40:29.915Z" }, ... ]
    deactivate server

    Note over browser,server: The browser executes the callback function that <br/> renders the notes
```

# 0.6: New note on single-page application diagram

``` mermaid
sequenceDiagram
    participant browser 
    participant server

    browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note over browser,server: Request Payload  <br/> [{ "content": "hola buenas tardes", "date": "2024-03-27T17:40:29.915Z" }, ... ]<br/>content: "prueba4"<br/> date:"2024-03-28T02:01:27.424Z"
    server-->>browser: Status Code :201 Create
    deactivate server
    
    Note over browser,server: The browser executes the callback function that <br/> renders the notes   
```
