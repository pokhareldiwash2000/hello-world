<details>
<summary>User Creation & Authentication</summary>
Register User
User Login
User Logout
User Authentication with Google
</details>
<details>
<summary>User Account Functionalities</summary>
Get User Profile
Delete User Account
Update User Account
Upload/Change Profile Picture
</details>
<details>
<summary>Admin Functionalities</summary>
Register New Admin User
Get All Current Users
Get User Information by ID
Get Own Profile Information (Admin)
Get User Information by Email (Admin)
Delete User by ID
Delete Comment by ID
Delete Post by ID
</details>
<details>
<summary>Admin Functionality for Managing Site's Resources</summary>
Upload Photo
Upload Video
Delete Photo
Delete Video
Get Uploaded Photos
</details>
<details>
<summary>Admin Functionality for Handling Mails</summary>
Send Mail
Get All Mails
Get Mail by ID
Delete Mail by ID
</details>
<details>
<summary>Dashboard Posts Related Functionalities</summary>
Get All Posts
Get Post by ID
</details>
<details>
<summary>User's Personal Control Over Creation of Posts</summary>
Get User's Posts
Get Post by ID (User)
Create New Post
Update Post
Delete Post
</details>
<details>
<summary>Commenting Related Functionalities</summary>
Create New Comment
Edit Comment
Delete Comment
</details>
<details>
<summary>Searching and Filtering Routes</summary>
Search Posts
Filter Posts
</details>



API Documentation
User Creation & Authentication
Register User
Endpoint: POST /api/user/register
Description: Register a new user.
Request Body:
name (string): User's name.
email (string): User's email.
password (string): User's password.
Response: None
User Login
Endpoint: POST /api/user/login
Description: User login.
Request Body:
name (string): User's name.
email (string): User's email.
Response:
auth-token (string): Token to be added to the header on subsequent requests to maintain session.
User Logout
Endpoint: POST /api/user/logout
Description: User logout.
Request Header:
auth-token (string): User's authentication token.
Response: None
User Authentication with Google
Endpoint: POST /api/user/auth/google
Description: Sign up or login with Google.
Response:
auth-token (string): Token for authentication.
User Account Functionalities
Get User Profile
Endpoint: GET /api/account
Description: Get the profile information of the authenticated user.
Response: User profile information.
Delete User Account
Endpoint: DELETE /api/account/:id
Description: Delete the authenticated user's account.
Response: None
Update User Account
Endpoint: PUT /api/account/:id
Description: Update the username or password of the authenticated user.
Request Body (either of the following):
name (string): New username.
password (string): New password.
Response: Updated user account information.
Upload/Change Profile Picture
Endpoint: POST /api/account/profile-picture
Description: Upload or change the profile picture of the authenticated user.
Request Body: File (form-data) under the key photo.
Response: None
Admin Functionalities
Register New Admin User
Endpoint: POST /api/admin/register
Description: Register a new admin user.
Response: None
Get All Current Users
Endpoint: GET /api/admin/all
Description: Get information for all current users.
Query Parameters:
limit (number, optional): Limit the number of users returned per page.
page (number, optional): Specify the page number.
Response: Information for all current users.
Get User Information by ID
Endpoint: GET /api/admin/finduser/:id
Description: Get user information by ID.
Response: User information for the specified ID.
Get Own Profile Information (Admin)
Endpoint: GET /api/admin/findme
Description: Get own profile information (admin).
Response: Admin's profile information.
Get User Information by Email (Admin)
Endpoint: GET /api/admin/finduser
Description: Get user information by email.
Query Parameter:
email (string): User's email to search for.
Response: User information for the specified email.
Delete User by ID
Endpoint: DELETE /deleteuser/:id
Description: Delete a user by ID.
Response: Deleted user object.
Delete Comment by ID
Endpoint: DELETE /deletecomment/:id
Description: Delete a comment by ID.
Response: Deleted comment object.
Delete Post by ID
Endpoint: DELETE /deletepost/:id
Description: Delete a post by ID.
Response: Deleted post object.
Admin Functionality for Managing Site's Resources
Upload Photo
Endpoint: POST /api/admin/upload/photo
Description: Upload a photo.
Request Body: Photo file (form data).
Response: None
Upload Video
Endpoint: POST /api/admin/upload/video
Description: Upload a video.
Request Body: Video file (form data).
Response: None
Delete Photo
Endpoint: DELETE /api/admin/remove/photo/:filename
Description: Delete a photo.
Response: None
Delete Video
Endpoint: DELETE /api/admin/remove/video/:filename
Description: Delete a video.
Response: None
Get Uploaded Photos
Endpoint: GET /photos
Description: Get a list of uploaded photos.
Response: List of uploaded photos.
Get Uploaded Videos
Endpoint: GET /videos
Description: Get a list of uploaded videos.
Response: List of uploaded videos.
Admin Functionality for Handling Mails
Send Mail
Endpoint: POST /api/mails
Description: Send a mail.
Request Body:
name (string): Sender's name.
email (string): Sender's email.
message (string): Mail message.
Response: None
Get All Mails
Endpoint: GET /api/mails
Description: Get all the mails.
Response: All the mails.
Get Mail by ID
Endpoint: GET /api/mails/:id
Description: Get a specific mail by ID.
Response: Mail with the specified ID.
Delete Mail by ID
Endpoint: DELETE /api/mails/:id
Description: Delete a particular mail by ID.
Response: None
Dashboard Posts Related Functionalities
Get All Posts
Endpoint: GET /api/posts
Description: Get posts from the database.
Query Parameters:
cuisine (string, optional): Filter posts based on cuisine category.
course (string, optional): Filter posts based on course category.
diet (string, optional): Filter posts based on diet category.
limit (number, optional): Limit the number of posts to be retrieved.
Response: Posts matching the query parameters.
Get Post by ID
Endpoint: GET /api/posts/:id
Description: Get a single post by ID.
Response: Post with the specified ID.
User's Personal Control Over Creation of Posts
Important: All uploads to the following routes should be made as multipart/form-data, not application/json.

Get User's Posts
Endpoint: GET /api/myposts
Description: Get all posts or filter posts by cuisine, course, or diet.
Query Parameters:
cuisine (string, optional): Filter posts by cuisine category.
course (string, optional): Filter posts by course category.
diet (string, optional): Filter posts by diet category.
limit (number, optional): Limit the number of posts to be retrieved.
Response: JSON array of posts.
Get Post by ID (User)
Endpoint: GET /api/myposts/:id
Description: Get post by ID.
Response: Post object or 404 error if the post is not found.
Create New Post
Endpoint: POST /api/myposts
Description: Create a new post.
Request Body Parameters:
name (string): Post name.
description (string): Post description.
photo (file): Post photo.
youtubeURL (string): YouTube URL for the post.
servings (string): Number of servings.
cookingTime (string): Cooking time.
prepTime (string): Preparation time.
ingredients (string): Post ingredients.
steps (string): Post steps.
cuisinecategory (string): Post cuisine category.
coursecategory (string): Post course category.
dietcategory (string): Post diet category.
Response: Created post object or 500 error if failed to create post.
Update Post
Endpoint: PATCH /api/myposts/:id
Description: Update a post with the specified ID.
Authentication: User must be verified.
Request Body: Fields to update in the post.
Response: Updated post object.
Delete Post
Endpoint: DELETE /api/myposts/:id
Description: Delete a post with the specified ID.
Authentication: User must be verified.
Response: Deleted post object.
Commenting Related Functionalities
Create New Comment
Endpoint: POST /api/comment
Authorization Required: Yes
Request Body:
post (string): ID of the post.
text (string): Comment text.
rating (number): Comment rating.
Response: None
Edit Comment
Endpoint: PATCH /api/comment/:id
Authorization Required: Yes
Request Body:
text (string): Updated comment text.
rating (number): Updated comment rating.
Response: None
Delete Comment
Endpoint: DELETE /api/comment/:id
Authorization Required: Yes
Response: None
Searching and Filtering Routes
Search Posts
Endpoint: GET /api/search?q=search-term
Description: Search for posts in the database that match the specified search term using fuzzy matching.
Query Parameters:
q (string): The search term to match.
Response: JSON object containing the matched posts or an error message if unsuccessful.
Filter Posts
Endpoint: GET /api/search/filter
Description: Filter posts in the database based on specified cuisine, course, and diet categories. Returns a list of filtered posts.
Query Parameters:
cuisine (string): Cuisine categories to filter by (comma-separated).
course (string): Course categories to filter by (comma-separated).
diet (string): Diet categories to filter by (comma-separated).
Response: JSON object containing the filtered posts or an error message if unsuccessful.
Filtering Functionalities
You can filter by visiting the following routes:

GET /api/filter/new: Filter by new posts.
GET /api/filter/most-viewed: Filter by most viewed posts.
GET /api/filter/most-interacted: Filter by most interacted posts.
GET /api/filter/popular: Filter by popular posts.
GET /api/filter/trending: Filter by trending posts.
You can also send pagination and limit as query parameters. By default, page=1 and limit=10.
