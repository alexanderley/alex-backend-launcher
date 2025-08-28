### API Documentation
This is a good starter project if you want to build your own REST API. You can create users, generate session tokens, and validate routes. It also works seamlessly with the frontend launcher I’ve built in my other repositories.

If you’re using a SQL database, you’ll also find an alternative version available in the repos.

Have fun building!

### Tech Stack
- Node.js + express.js
- MongoDB for database
- .env for enviourmental variables
- bycrypt for password encryption
- jwt token for validation

### How to start?
- clone repo
- npm install
- npm run dev
- create a .env file
- server should run on http://localhost:5005/

#### Routes

##### Project routes

| HTTP verb | URL                        | Request body | Action                        |
| --------- | -------------------------- | ------------ | ----------------------------- |
| GET       | `/api/projects`            | (empty)      | Returns all the projects      |
| POST      | `/api/projects`            | JSON         | Adds a new project            |
| GET       | `/api/projects/:projectId` | (empty)      | Returns the specified project |
| PUT       | `/api/projects/:projectId` | JSON         | Edits the specified project   |
| DELETE    | `/api/projects/:projectId` | (empty)      | Deletes the specified project |

##### Task routes

| HTTP verb | URL                  | Request body | Action                     |
| --------- | -------------------- | ------------ | -------------------------- |
| POST      | `/api/tasks`         | JSON         | Adds a new task            |
| GET       | `/api/tasks/:taskId` | (empty)      | Returns the specified task |
| PUT       | `/api/tasks/:taskId` | JSON         | Edits the specified task   |
| DELETE    | `/api/tasks/:taskId` | (empty)      | Deletes the specified task |



##### Auth routes

| HTTP verb | URL            | Request Headers                 | Request Body              |
| --------- | -------------- | ------------------------------- | ------------------------- |
| POST      | `/auth/signup` | --                              | { email, password, name } |
| POST      | `/auth/login`  | --                              | { email, password }       |
| GET       | `/auth/verify` | Authorization: Bearer \< JWT \> | --                        |



<hr>

#### Models

##### Project Model

```js
{
  title: String,
  description: String,
  tasks: [ { type: Schema.Types.ObjectId, ref: 'Task' } ]
}
```

##### Task Model

```js
{
  title: String,
  description: String,
  project: { type: Schema.Types.ObjectId, ref: 'Project' }
}
```

##### User Model

```js
{
  email: { type: String, unique: true, required: true },
  password: { type: String, required: true },
  name: { type: String, required: true },
}
```

