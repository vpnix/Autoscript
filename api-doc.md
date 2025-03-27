# VPNix API Documentation

## Authentication

All API requests require authentication using an API key. The API key must be provided in the `X-API-Key` header.

Example:
```
X-API-Key: your_api_key_here
```

## API Responses

All API responses follow a standard format:

```json
{
  "success": true,
  "message": "Operation successful message",
  "data": { ... },
  "error": "Error message if success is false"
}
```

## User Management

### List All Users
- **URL**: `/api/users`
- **Method**: `GET`
- **Description**: Retrieves a list of all users in the system

**Response Example**:
```json
{
  "success": true,
  "message": "Users retrieved successfully",
  "data": [
    {
      "id": 1,
      "name": "user1",
      "uuid": "123e4567-e89b-12d3-a456-426614174000",
      "protocol": "vmess",
      "status": "active",
      "usage": 1073741824,
      "limit_quota": 10737418240,
      "limit_ip": 2,
      "created_at": "2023-01-01T00:00:00Z",
      "expired_at": "2023-02-01T00:00:00Z",
      "vmess_link_tls": "vmess://...",
      "vmess_link_ntls": "vmess://...",
      "path_vmess": "/vpnix"
    }
  ]
}
```

### Create User
- **URL**: `/api/users`
- **Method**: `POST`
- **Description**: Creates a new user

**Request Body**:
```json
{
  "name": "username",
  "protocol": "vmess",
  "limit_quota": 10,
  "limit_ip": 2,
  "expire_days": 30,
  "is_trial": false
}
```

- `name`: Username (required)
- `protocol`: Connection protocol (required, can be "vmess", "vless", or "trojan")
- `limit_quota`: Data quota in GB (required for non-trial users)
- `limit_ip`: Maximum simultaneous connections allowed (required for non-trial users)
- `expire_days`: Number of days until account expires (required for non-trial users)
- `is_trial`: Whether this is a trial account (boolean, optional)

**Response Example**:
```json
{
    "success": true,
    "message": "User created successfully",
    "data": {
        "expired_at": "2025-04-26T17:33:42.96868461+07:00",
        "id": 123,
        "name": "testapi1",
        "path_trojan": "/trojanWS",
        "path_vless": "/vlessWS",
        "path_vmess": "/vmessWS",
        "protocol": "vmess,vless,trojan",
        "status": "active",
        "trojan_link_tls": "trojan://xxxx",
        "uuid": "xxxx",
        "vless_link_ntls": "vless://xxxx",
        "vless_link_tls": "vless://xxxx",
        "vmess_link_ntls": "vmess://xxxx",
        "vmess_link_tls": "vmess://xxxx="
    }
}
```

### Get User Details
- **URL**: `/api/users/{username}`
- **Method**: `GET`
- **Description**: Retrieves details for a specific user

**Response Example**:
```json
{
  "success": true,
  "message": "User retrieved successfully",
  "data": {
    "id": 1,
    "name": "username",
    "uuid": "123e4567-e89b-12d3-a456-426614174000",
    "protocol": "vmess",
    "status": "active",
    "usage": 1073741824,
    "limit_quota": 10737418240,
    "limit_ip": 2,
    "created_at": "2023-01-01T00:00:00Z",
    "expired_at": "2023-02-01T00:00:00Z",
    "vmess_link_tls": "vmess://...",
    "vmess_link_ntls": "vmess://...",
    "path_vmess": "/vpnix"
  }
}
```

### Update User
- **URL**: `/api/users/{username}`
- **Method**: `PUT` or `PATCH`
- **Description**: Updates an existing user

**Request Body**:
```json
{
  "name": "new_username",
  "protocol": "vless",
  "limit_quota": 20,
  "limit_ip": 3,
  "expire_days": 60,
  "status": "active",
  "reset_usage": true
}
```

All fields are optional. Only the fields you want to update need to be included.

- `name`: New username
- `protocol`: New connection protocol (can be "vmess", "vless", or "trojan")
- `limit_quota`: New data quota in GB
- `limit_ip`: New maximum simultaneous connections allowed
- `expire_days`: Number of days to set for expiration (calculated from current date)
- `status`: New status (can be "active", "suspended", "expired", or "quota_exceeded")
- `reset_usage`: Whether to reset the usage counter (boolean)

**Response Example**:
```json
{
  "success": true,
  "message": "User updated successfully",
  "data": {
    "id": 1,
    "name": "new_username",
    "status": "active",
    "protocol": "vless"
  }
}
```

### Delete User
- **URL**: `/api/users/{username}`
- **Method**: `DELETE`
- **Description**: Deletes a user

**Response Example**:
```json
{
  "success": true,
  "message": "User deleted successfully",
  "data": {
    "id": 1,
    "name": "username"
  }
}
```

### Extend User Expiry
- **URL**: `/api/users/{username}/extend`
- **Method**: `POST`
- **Description**: Extends a user's expiry date

**Request Body**:
```json
{
  "days": 30
}
```

- `days`: Number of days to extend the expiry by (required, must be > 0)

**Response Example**:
```json
{
  "success": true,
  "message": "User expiry extended successfully",
  "data": {
    "id": 1,
    "name": "username",
    "expired_at": "2023-03-01T00:00:00Z"
  }
}
```

### Suspend User
- **URL**: `/api/users/{username}/suspend`
- **Method**: `POST`
- **Description**: Suspends a user account

**Response Example**:
```json
{
  "success": true,
  "message": "User suspended successfully",
  "data": {
    "id": 1,
    "name": "username",
    "status": "suspended",
    "suspended_at": "2023-01-15T00:00:00Z"
  }
}
```

### Unsuspend User
- **URL**: `/api/users/{username}/unsuspend`
- **Method**: `POST`
- **Description**: Unsuspends a previously suspended user account

**Response Example**:
```json
{
  "success": true,
  "message": "User unsuspended successfully",
  "data": {
    "id": 1,
    "name": "username",
    "status": "active"
  }
}
```

## System Information

### Get System Information
- **URL**: `/api/system/info`
- **Method**: `GET`
- **Description**: Retrieves basic system information

**Response Example**:
```json
{
  "success": true,
  "message": "System information retrieved successfully",
  "data": {
    "hostname": "vpnix-server",
    "domain": "vpnix.example.com",
    "version": "1.0.0",
    "xray_status": "Running",
    "uptime": "15 days, 7 hours, 23 minutes",
    "time": "2023-01-15T12:34:56Z"
  }
}
```

### Get System Statistics
- **URL**: `/api/system/stats`
- **Method**: `GET`
- **Description**: Retrieves detailed system statistics

**Response Example**:
```json
{
  "success": true,
  "message": "System stats retrieved successfully",
  "data": {
    "users": {
      "total": 100,
      "active": 75,
      "suspended": 10,
      "expired": 12,
      "quota_exceeded": 3,
      "expiring_soon": 8
    },
    "resources": {
      "cpu_usage": 25.5,
      "memory_usage": 40.2,
      "disk_usage": 35.7
    }
  }
}
```

## Backup Management

### List Backups
- **URL**: `/api/backups`
- **Method**: `GET`
- **Description**: Retrieves a list of all backups

**Response Example**:
```json
{
  "success": true,
  "message": "Backups retrieved successfully",
  "data": [
    {
      "file": "backup_2023-01-15.zip",
      "path": "/path/to/backup_2023-01-15.zip",
      "size": 1048576,
      "created_at": "2023-01-15T00:00:00Z"
    }
  ]
}
```

### Create Backup
- **URL**: `/api/backups`
- **Method**: `POST`
- **Description**: Creates a new backup

**Response Example**:
```json
{
  "success": true,
  "message": "Backup created successfully",
  "data": {
    "file": "backup_2023-01-15.zip",
    "path": "/path/to/backup_2023-01-15.zip",
    "size": 1048576
  }
}
```

### Download Backup
- **URL**: `/api/backups/{filename}`
- **Method**: `GET`
- **Description**: Downloads a specific backup file
- **Response**: The backup file as a binary download

## Error Handling

If an error occurs, the API will return an appropriate HTTP status code along with an error message:

```json
{
  "success": false,
  "error": "Error message explaining what went wrong"
}
```

Common HTTP status codes:
- `400 Bad Request`: Invalid input, missing required fields
- `401 Unauthorized`: Invalid or missing API key
- `404 Not Found`: Resource not found
- `405 Method Not Allowed`: Wrong HTTP method used
- `500 Internal Server Error`: Server-side error

## Rate Limiting

API requests are subject to rate limiting to prevent abuse. If you exceed the rate limit, you will receive a `429 Too Many Requests` response.
