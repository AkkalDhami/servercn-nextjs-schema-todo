# Todo Application

This repository contains the backend schemas and models for a Todo application, demonstrating implementations across different database technologies: MySQL, MongoDB, and PostgreSQL. Each database implementation provides schemas/models for `User` and `Todo` entities.

## Database Implementations

### 1. MySQL (using Drizzle ORM)

The MySQL implementation uses Drizzle ORM for defining database schemas and interacting with the database.

#### User Schema (`user.schema.ts`)

The `users` table stores user information with the following key fields:

- `id`: Primary key, auto-incrementing integer.
- `name`: User's full name.
- `email`: User's unique email address, used for login.
- `password`: Hashed password for local authentication.
- `role`: User's role (e.g., 'user', 'admin').
- `provider`: Authentication provider (e.g., 'local', 'google', 'github').
- `providerId`: ID from the external authentication provider.
- `avatar`: JSON object storing avatar details (public_id, url, size).
- `isEmailVerified`: Boolean indicating if the email has been verified.
- `lastLoginAt`: Timestamp of the last login.
- `failedLoginAttempts`: Count of consecutive failed login attempts.
- `lockUntil`: Timestamp until which the account is locked after too many failed attempts.
- `isDeleted`: Soft delete flag.
- `deletedAt`: Timestamp when the user was soft-deleted.
- `reActivateAvailableAt`: Timestamp when account reactivation is available.
- `createdAt`: Timestamp of user creation.
- `updatedAt`: Timestamp of last update.

#### Todo Schema (`todo.schema.ts`)

The `todos` table stores individual todo items, linked to a user:

- `id`: Primary key, auto-incrementing integer.
- `userId`: Foreign key referencing the `users` table (onDelete: cascade).
- `title`: Title of the todo item.
- `description`: Optional detailed description of the todo item.
- `completed`: Boolean indicating if the todo item is completed.
- `createdAt`: Timestamp of todo creation.
- `updatedAt`: Timestamp of last update.

### 2. MongoDB (using Mongoose)

The MongoDB implementation uses Mongoose for defining schemas and interacting with the NoSQL database.

#### User Model (`user.model.ts`)

The `User` model defines the structure for user documents:

- `_id`: MongoDB's default primary key.
- `name`: User's full name.
- `email`: User's unique email address, used for login.
- `password`: Hashed password for local authentication.
- `role`: User's role (e.g., 'user', 'admin').
- `provider`: Authentication provider (e.g., 'local', 'google', 'github').
- `providerId`: ID from the external authentication provider.
- `avatar`: Object storing avatar details (public_id, url, size).
- `isEmailVerified`: Boolean indicating if the email has been verified.
- `lastLoginAt`: Timestamp of the last login.
- `failedLoginAttempts`: Count of consecutive failed login attempts.
- `lockUntil`: Timestamp until which the account is locked.
- `isDeleted`: Soft delete flag.
- `deletedAt`: Timestamp when the user was soft-deleted.
- `reActivateAvailableAt`: Timestamp when account reactivation is available.
- `createdAt`: Timestamp of user creation (managed by Mongoose `timestamps`).
- `updatedAt`: Timestamp of last update (managed by Mongoose `timestamps`).

#### Todo Model (`todo.model.ts`)

The `Todo` model defines the structure for todo item documents:

- `_id`: MongoDB's default primary key.
- `userId`: Reference to the `User` model.
- `title`: Title of the todo item.
- `description`: Optional detailed description of the todo item.
- `completed`: Boolean indicating if the todo item is completed.
- `createdAt`: Timestamp of todo creation (managed by Mongoose `timestamps`).
- `updatedAt`: Timestamp of last update (managed by Mongoose `timestamps`).

### 3. PostgreSQL (using Drizzle ORM)

The PostgreSQL implementation uses Drizzle ORM for defining database schemas and interacting with the database.

#### User Schema (`user.schema.ts`)

The `users` table stores user information with the following key fields:

- `id`: Primary key, serial integer.
- `name`: User's full name.
- `email`: User's unique email address, used for login.
- `password`: Hashed password for local authentication.
- `role`: User's role (e.g., 'user', 'admin'), defined using `pgEnum`.
- `provider`: Authentication provider (e.g., 'local', 'google', 'github'), defined using `pgEnum`.
- `providerId`: ID from the external authentication provider.
- `avatar`: JSON object storing avatar details (public_id, url, size).
- `isEmailVerified`: Boolean indicating if the email has been verified.
- `lastLoginAt`: Timestamp of the last login.
- `failedLoginAttempts`: Count of consecutive failed login attempts.
- `lockUntil`: Timestamp until which the account is locked.
- `isDeleted`: Soft delete flag.
- `deletedAt`: Timestamp when the user was soft-deleted.
- `reActivateAvailableAt`: Timestamp when account reactivation is available.
- `createdAt`: Timestamp of user creation.
- `updatedAt`: Timestamp of last update.

#### Todo Schema (`todo.schema.ts`)

The `todos` table stores individual todo items, linked to a user:

- `id`: Primary key, serial integer.
- `userId`: Foreign key referencing the `users` table (onDelete: cascade).
- `title`: Title of the todo item.
- `description`: Optional detailed description of the todo item.
- `completed`: Boolean indicating if the todo item is completed.
- `createdAt`: Timestamp of todo creation.
- `updatedAt`: Timestamp of last update.
