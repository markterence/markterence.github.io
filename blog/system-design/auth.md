# Designing Auth systems


## Schema

### User 

| Field         | Data Type | Key | Description                                      |
|---------------|-----------|-----|--------------------------------------------------|
| id            | varchar(36)    | PK  | Unique identifier for each user                 |
| name          | text    | Not Null   | User's chosen display name                      |
| email         | varchar(255)    |  Not Null   | User's email address used for login and comms   |
| emailVerified | boolean   |  Not Null   | Whether the user's email is verified            |
| image         | string    |    | User's image URL                                |
| createdAt     | Datetime      | Not Null   | Timestamp of when the user account was created  |
| updatedAt     | Datetime      | Not Null   | Timestamp of the last update to the user's info |
