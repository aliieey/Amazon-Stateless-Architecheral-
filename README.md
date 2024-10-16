# Amazon-Stateless-Architecheral-
Amazon Stateless Architecheral Structure Assignment.

Here are the simplified explanations with accompanying diagrams to illustrate stateless architecture, authentication, and authorization used by Amazon:

Stateless Architecture

1. Request-Response Model
Each user request is independent, with all necessary information sent with each request. The server does not remember previous requests.

Diagram:

User ----> Request ----> Server
          (No State)    


2. Data Retrieval
The server handles each request independently without storing any previous data, reducing the load on the database.

Diagram:

User ----> Request 1 ----> Server (Handles independently)
User ----> Request 2 ----> Server (Handles independently)




Authentication

1. User Credentials
Users log in with a username and password. The server validates these credentials and provides an access token.

Diagram:

User ----> Login (Username & Password) ----> Server
           (Validates)                    ----> Access Token


2. Token Generation
The server generates a JWT (JSON Web Token) that is securely signed, ensuring it cannot be altered.

Diagram:

Server ----> Generate JWT ----> User


3. Token Expiration
The token has an expiration time and becomes invalid after a certain period. Users must renew the token to continue using the service.

Diagram:

User ----> Request with Token ----> Server
           (Checks Expiration)


4. Sessionless
The server does not store session states. Each request includes the token for validation.

Diagram:

User ----> Request with Token ----> Server
            (Validates Token)


Authorization

1. Access Control Lists (ACLs)
Amazon uses ACLs to define who can access specific resources.

Diagram:

          Resource
           +------+
User ----> ACLs ----> Access Control
           +------+


2. Claims-Based Authorization
JWT tokens include claims that specify user permissions, which the server checks before allowing actions.

Diagram:

User ----> Request with Token ----> Server
           (Checks Claims)          ----> Access Granted/Denied


3. Role-Based Access Control (RBAC)
Users are assigned roles (like "Admin" or "Customer") with specific permissions.

Diagram:

            Role
         +----------+
User ----> Role ----> Permissions
         +----------+


4. Fine-Grained Access Control
Authorization controls access to specific actions based on user permissions.

Diagram:

User ----> Action Request ----> Server
           (Checks Permissions) ----> Access Granted/Denied



