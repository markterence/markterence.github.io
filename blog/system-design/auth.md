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

### Session

| Field       | Data Type | Key          | Description                                     |
|-------------|-----------|--------------|-------------------------------------------------|
| id          | string    | PK           | Unique identifier for each session             |
| userId      | string    | FK(user.id)  | The ID of the user                             |
| token       | string    | -            | The unique session token                       |
| expiresAt   | Date      | -            | The time when the session expires              |
| ipAddress   | string    | -            | The IP address of the device                   |
| userAgent   | string    | -            | The user agent information of the device       |
| createdAt   | Date      | -            | Timestamp of when the session was created      |
| updatedAt   | Date      | -            | Timestamp of when the session was updated      |


### Account

| Field                  | Data Type | Key          | Description                                                                 |
|------------------------|-----------|--------------|-----------------------------------------------------------------------------|
| id                     | string    | PK           | Unique identifier for each account                                          |
| userId                 | string    | FK(user.id)  | The ID of the user                                                          |
| accountId              | string    | -            | The ID of the account from the SSO or equal to userId for credential login |
| providerId             | string    | -            | The ID of the provider                                                      |
| accessToken            | string    | -            | The access token returned by the provider                                   |
| refreshToken           | string    | -            | The refresh token returned by the provider                                  |
| accessTokenExpiresAt   | Date      | -            | The time when the access token expires                                      |
| refreshTokenExpiresAt  | Date      | -            | The time when the refresh token expires                                     |
| scope                  | string    | -            | The scope of the account returned by the provider                           |
| idToken                | string    | -            | The ID token returned from the provider                                     |
| password               | string    | -            | The password for the account (used for email/password auth)                 |
| createdAt              | Date      | -            | Timestamp of when the account was created                                   |
| updatedAt              | Date      | -            | Timestamp of when the account was updated                                   |


### Verification

| Field       | Data Type | Key | Description                                            |
|-------------|-----------|-----|--------------------------------------------------------|
| id          | string    | PK  | Unique identifier for each verification               |
| identifier  | string    | -   | The identifier for the verification request           |
| value       | string    | -   | The value to be verified                              |
| expiresAt   | Date      | -   | The time when the verification request expires        |
| createdAt   | Date      | -   | Timestamp of when the verification request was created|
| updatedAt   | Date      | -   | Timestamp of when the verification request was updated|


### JWKS

| Field      | Data Type | Key | Description                                  |
|------------|-----------|-----|----------------------------------------------|
| id         | string    | PK  | Unique identifier for each web key           |
| publicKey  | string    | -   | The public part of the web key               |
| privateKey | string    | -   | The private part of the web key              |
| createdAt  | Date      | -   | Timestamp of when the web key was created    |
