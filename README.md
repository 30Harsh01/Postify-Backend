Postify Backend

A lightweight social-interaction backend that demonstrates how discussions, comments, and likes are stored and managed like Instagram or Facebook.
Built with Node.js, Express, and MongoDB, it provides secure user auth and complete interaction features.
---

# 📘 **InstaTalk – Discussion, Comments & Likes API**

A simple backend project demonstrating how platforms like **Instagram** or **Facebook** store and manage **discussions, comments, and likes** using **Node.js, Express, and MongoDB**.
This project provides full authentication, discussion threads, user comments, and like/unlike features.

---

## 🚀 **Project Flow**

### **1. `conn.js`**

* Establishes a connection to MongoDB using Mongoose when the server starts.

### **2. `index.js`**

* Initializes Express server.
* Sets up CORS and JSON parsing middleware.
* Connects to MongoDB.
* Registers all route modules:

  * Auth
  * Discussion
  * Comments
  * Likes

### **3. `middleware/auth.js`**

* Verifies JWT tokens in protected routes.
* Attaches authenticated user data to the request object.
* Ensures only logged-in users access secured APIs.

---

## 📂 **Routes & Schemas**

### **🔐 Authentication (`routes/auth.js`)**

**Register User**

* Creates a new user.
* Hashes passwords using bcrypt.
* Returns JWT token.

**Login User**

* Validates email/mobile + password.
* Returns authentication token.

**Get User Details**

* Protected; returns logged-in user’s info.

**Update/Delete User**

* Only the authenticated user can modify their own account.

**Search User by Name**

* Protected; search users by name.

---

### 🗨️ **Discussion (`routes/discussion.js`)**

* **Create Discussion** (requires auth)
* **Fetch All Discussions**
* **Update/Delete Discussion** (owner-only)
* **Fetch Discussions by Tag**

---

### 💬 **Comments (`routes/comment.js`)**

* **Add Comment** to a discussion
* **Edit Comment** (owner-only)
* **Delete Comment** (owner-only)
* **Fetch Comments** for a discussion

---

### ❤️ **Likes (`routes/like.js`)**

Supports liking/unliking:

* Discussions
* Comments

---

## 🌐 **API Endpoints Overview**

### 👤 **User APIs**

| No | Method | Endpoint                  | Description                     |
| -- | ------ | ------------------------- | ------------------------------- |
| 1  | POST   | `/api/auth/createuser`    | Register new user               |
| 2  | POST   | `/api/auth/login`         | Login user & generate JWT       |
| 3  | GET    | `/api/auth/getusers`      | Fetch all users (protected)     |
| 4  | PUT    | `/api/auth/updateuser`    | Update logged-in user           |
| 5  | DELETE | `/api/auth/deleteuser`    | Delete own account              |
| 6  | GET    | `/api/auth/getuserbyname` | Search user by name (protected) |

---

### 🗨️ **Discussion APIs**

| Method | Endpoint                                | Description            |
| ------ | --------------------------------------- | ---------------------- |
| POST   | `/api/discussion/creatediscussion`      | Create a discussion    |
| GET    | `/api/discussion/fetchalldiscussions`   | Get all discussions    |
| PUT    | `/api/discussion/updatediscussion/:id`  | Update discussion      |
| DELETE | `/api/discussion/deletediscussion/:id`  | Delete discussion      |
| POST   | `/api/discussion/fetchdiscussionsbytag` | Get discussions by tag |

---

### 💬 **Comment APIs**

| Method | Endpoint                       | Description    |
| ------ | ------------------------------ | -------------- |
| POST   | `/api/comment/comment/:id`     | Add comment    |
| PUT    | `/api/comment/editcomment/:id` | Edit comment   |
| DELETE | `/api/comment/comment/:id`     | Delete comment |

---

### ❤️ **Like APIs**

| Method | Endpoint                           | Description         |
| ------ | ---------------------------------- | ------------------- |
| POST   | `/api/like/likeondiscussion/:id`   | Like a discussion   |
| POST   | `/api/like/unlikeondiscussion/:id` | Unlike a discussion |
| POST   | `/api/like/likeoncomment/:id`      | Like a comment      |
| POST   | `/api/like/unlikeoncomment/:id`    | Unlike a comment    |

---

## 📌 **Total APIs: 18**

---
