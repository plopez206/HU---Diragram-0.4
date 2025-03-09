# Diagrama: Creación de una Nota en la App

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Escribe una nota y presiona "Guardar"
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Server-->>Browser: Respuesta 201 Created
    deactivate Server

    Note right of Browser: La nota ha sido guardada en el servidor

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "Nueva Nota", "date": "2025-03-08" }, ... ]
    deactivate Server

    Note right of Browser: El navegador actualiza la lista de notas en la página
