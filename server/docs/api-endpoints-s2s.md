# API Endpoints (Prosody to API Server)

## Rooms

### Create Room

#### Create Room - Request

- URL
  - /api/v1/rooms
- Method
  - POST
- Header
  - Content-type: application/json
- Body
  - name - string
  - session - string
  - jid - string

#### Create Room - Response

- Successful operation (200)
  
    ```json
    {
        "status": "success",
        "message": "room created successfully"
    }
    ```

- Validation fail (422)
  
    ```json
    {
        "status": "invalid",
        "message": "room inputs validation fail"
    }
    ```

- Duplication fail (400)
  
    ```json
    {
        "status": "duplicate",
        "message": "room already exist with same session ID"
    }
    ```

### End room

#### Request

- URL
  - /api/v1/rooms/{session}
- Method
  - DELETE
- Header
  - Content-type: application/json
- URL Params
  - session
- Body
  - jid - string

#### Response

- Successful operation (200)
  
    ```json
    {
        "status": "success",
        "message": "room ended successfully"
    }
    ```

- Validation fail (422)
  
    ```json
    {
        "status": "invalid",
        "message": "room inputs validation fail"
    }
    ```

- Duplication fail (400)
  
    ```json
    {
        "status": "duplicate",
        "message": "room already exist with same session ID"
    }
    ```

- Room not exist (404)
  
    ```json
    {
        "status": "no-room",
        "message": "room record with session not exist"
    }
    ```

## Occupants

### Create occupant

#### Create occupant - Request

- URL
  - /api/v1/occupants
- Method
  - POST
- Header
  - Content-type: application/json
- Body
  - jid - string
  - roomJid - string
  - nick - string
  - role - string (participant/moderator)
  - email - string/optional
  - avatar - string/optional
  - userAgent - string/optional
  - ip - string/optional

#### Create occupant - Response

- Successful operation (200)
  
    ```json
    {
        "status": "success",
        "message": "occupant created successfully"
    }
    ```

- Validation fail (422)
  
    ```json
    {
        "status": "invalid",
        "message": "occupant inputs validation fail"
    }
    ```

- Duplication fail (400)
  
    ```json
    {
        "status": "duplicate",
        "message": "occupant already exist with same JID"
    }
    ```

- No Room fail (400)
  
    ```json
    {
        "status": "no-room",
        "message": "Cannot find room with roomJid"
    }
    ```

### Update occupant

#### Update occupant - Request

- URL
  - /api/v1/occupants/{jid}
- Method
  - PUT
- Header
  - Content-type: application/json
- URL Params
  - jid
- Body
  - roomJid - string
  - nick - string/optional
  - role - string/optional (participant/moderator)
  - email - string/optional

#### Update occupant - Response

- Successful operation (200)
  
    ```json
    {
        "status": "success",
        "message": "occupant updated successfully"
    }
    ```

- Validation fail (422)
  
    ```json
    {
        "status": "invalid",
        "message": "occupant inputs validation fail"
    }
    ```

- No occupant fail (400)
  
    ```json
    {
        "status": "no-occupant",
        "message": "Cannot find occupant with jid"
    }
    ```

### Destroy occupant

#### Destroy occupant - Request

- URL
  - /api/v1/occupants/{jid}
- Method
  - DELETE
- Header
  - Content-type: application/json
- URL Params
  - jid
- Body
  - roomJid - string

#### Destroy occupant - Response

- Successful operation (200)
  
    ```json
    {
        "status": "success",
        "message": "occupant destroyed successfully"
    }
    ```

- Validation fail (422)
  
    ```json
    {
        "status": "invalid",
        "message": "occupant inputs validation fail"
    }
    ```

- No occupant fail (400)
  
    ```json
    {
        "status": "no-occupant",
        "message": "Cannot find occupant with jid"
    }
    ```
