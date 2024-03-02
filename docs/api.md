

## /api

### GET /api/list
(only with auth)
Lists all files, associated with the current user
```json
[
    {
        "id": uuid,
        "name": string,
        "icon": url,
        
        "exp": timestamp,
        "enc": boolean,
        "name_enc": boolean, 
        "password": boolean,

        "download_id": string
    },
]
```

### GET /api/<file-id>/
(only with auth)
Returns the information of a single file
```json
{
    "id": uuid,
    "name": string (base64 encode if encrypted),
    "icon": url,
    
    "exp": timestamp,
    "remaining_downloads": number,
    "burn_after_disable": boolean, 
    "enc": boolean,
    "name_enc": boolean, 
    "password": boolean,

    "download_id": string
},
```

### PUT /api/<file-id>/
(only with auth)
Updates Configuration
Warning: enc, name_enc cannot be changed

### DELETE /api/<file-id>/
(only with auth)
Deletes a file imitated

### POST /api/<file-id>/password
(only with auth)
Updates/Sets Password hash (sha256-hash)

Req-Body:
```json
"<hash>"
```

### POST /api/<file-id>/reroll
(only with auth)
Rerolls the download_id

### GET /api/download/<download_id>/
Returns the raw file data.
If password protected this is needed:
```HTTP
Authorization: Basic <credentials>
```

### GET /api/download/<download_id>/info
Returns Information about the file
```json
{
    "id": uuid,
    "name": string (base64 encode if encrypted),
    "icon": url,
    
    "exp": timestamp,
    "enc": boolean,
    "name_enc": boolean, 
    "password": boolean,

    "download_id": string
}
```