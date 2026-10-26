# Personal Bookmark Manager

This application follows the Passport and database structure from `savage-auth`. Users can sign up, log in, and create, view, edit, open, and delete their own bookmarks.

## Configure MongoDB Atlas

Create a file named `atlas-credentials.env` in this folder. Use the connection details provided by MongoDB Atlas:

```dotenv
MONGODB_USERNAME="your_database_username"
MONGODB_PASSWORD="your_database_password"
MONGODB_URI="mongodb+srv://your_database_username:your_url_encoded_password@your_cluster_host/personal_bookmark_manager?retryWrites=true&w=majority"
```

Use your actual cluster host and credentials. URL-encode reserved characters in the password. Include `personal_bookmark_manager` as the database name in the URI path before the query string. The application reads `MONGODB_URI`; it does not use the username and password variables separately.

Do not commit `atlas-credentials.env`. The `.gitignore` file excludes environment files and `node_modules`.

## Start the application

Run these commands from this folder:

```powershell
npm install
npm start
```

The start script loads `atlas-credentials.env` with Node.js's built-in `--env-file` option. The application explicitly selects `personal_bookmark_manager` and starts listening only after the MongoDB Atlas connection succeeds. It does not use a local MongoDB server.

Open http://localhost:3002.

## CRUD

- Create: add a bookmark.
- Read: view saved bookmarks.
- Update: choose Edit and save the title or URL.
- Delete: choose Delete.

Each bookmark query is scoped to the logged-in user's account.
