# MySQL Database Schema

## Users Table

This table stores user information, including details required for authentication and authorization.

| Field         | Type         | Description                           |
|---------------|--------------|---------------------------------------|
| id            | INT          | Primary key, auto-increment           |
| auth0_id      | VARCHAR(255) | User ID from Auth0                    |
| username      | VARCHAR(50)  | Username                              |
| email         | VARCHAR(255) | Email address                         |
| password_hash | VARCHAR(255) | Encrypted password                    |
| created_at    | TIMESTAMP    | Timestamp of user creation            |
| updated_at    | TIMESTAMP    | Timestamp of last update              |

## Content Table

This table stores website content, including pages such as homepage, news, gigs, photos, and videos.

| Field         | Type         | Description                           |
|---------------|--------------|---------------------------------------|
| id            | INT          | Primary key, auto-increment           |
| title         | VARCHAR(255) | Title of the content                  |
| body          | TEXT         | Body/content of the content           |
| author_id     | INT          | Foreign key referencing Users table   |
| created_at    | TIMESTAMP    | Timestamp of content creation         |
| updated_at    | TIMESTAMP    | Timestamp of last update              |

## Authentication Tokens Table

This table stores authentication tokens issued by Auth0 for users.

| Field               | Type         | Description                            |
|---------------------|--------------|----------------------------------------|
| id                  | INT          | Primary key, auto-increment            |
| user_id             | INT          | Foreign key referencing Users table    |
| token_value         | VARCHAR(255) | Authentication token value             |
| expiration_timestamp| TIMESTAMP    | Expiration timestamp of the token      |
| created_at          | TIMESTAMP    | Timestamp of token creation            |

## Sessions Table

This table stores session information for users, tracking active sessions and associated user IDs.

| Field         | Type         | Description                           |
|---------------|--------------|---------------------------------------|
| id            | INT          | Primary key, auto-increment           |
| user_id       | INT          | Foreign key referencing Users table   |
| session_token | VARCHAR(255) | Session token                         |
| created_at    | TIMESTAMP    | Timestamp of session creation         |

