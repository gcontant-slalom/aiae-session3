# Cloud Architecture Overview

This document includes both a high-level system context view and a runtime sequence view for the Todo monorepo.

## System Context

This diagram shows the high-level system context for the monorepo: a React frontend calling an Express API backed by an in-memory task store.

```mermaid
flowchart LR
    user["User"] --> browser["Browser"]

    subgraph monorepo["aiae-session3 monorepo"]
        frontend["React frontend\npackages/frontend"]
        api["Express API\npackages/backend"]
        store[("In-memory task store\nbetter-sqlite3 / SQLite")]
    end

    browser --> frontend
    frontend -->|HTTP /api/tasks| api
    api -->|SQL queries| store
```

## Create TODO Sequence

This sequence diagram shows the runtime flow for a user creating a TODO in the monorepo application.

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant Store as In-memory Store

    User->>Frontend: Enter task details and submit
    Frontend->>Frontend: Validate title and build payload
    Frontend->>+API: POST /api/tasks
    API->>API: Validate request body
    API->>+Store: Insert task record
    Store-->>-API: Return created task
    API-->>-Frontend: 201 Created with task JSON
    Frontend->>+API: GET /api/tasks
    API->>+Store: Query current tasks
    Store-->>-API: Return task list
    API-->>-Frontend: 200 OK with tasks
    Frontend-->>User: Show new TODO in the list
```