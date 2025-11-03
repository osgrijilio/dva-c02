# IAM

## Authentication

Via IAM users.

Authentication is the process to verify someone is the person it says they are, because the have the proper credentials.

Authentication ensures that the user is who they say they are. User names and passwords are the most common types of authentication. But you might also work with other forms, such as token-based authentication or biometric data, like a fingerprint. Authentication simply answers the question, “Are you who you say you are?”

## Authorization

Via IAM policies attached to users (identities, in general).

Authorization check the user has the permissions that state what you can or cannot do.

Authorization is the process of giving users permission to access AWS resources and services. Authorization determines whether a user can perform certain actions, such as read, edit, delete, or create resources. Authorization answers the question, “What actions can you perform?” 

Policies are expressed as JSON documents.

You cannot apply policies to the root user, so it's convenient to create an IAMM admin user that can have policies in place.