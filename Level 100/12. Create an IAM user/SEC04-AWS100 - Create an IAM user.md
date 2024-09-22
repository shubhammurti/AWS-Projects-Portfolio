# SEC04-AWS100 — Create an IAM user

## Cloud Service Provider

* Amazon Web Services

## Difficulty
* Level 100 (Introductory)

## Estimated time:
 * 1 hour

## Cost
* IAM is a free service

## Project's Author(s)
* [Syed Auther](https://twitter.com/syedauther)

## Objectives

### You need to complete the following:

* Create a new user in IAM with console access
* Add the user to an Admin group 
  * Create a new group called "Admins"
  * Add the `AdministratorAccess` managed policy to the new group
  * Add your new user to the "Admins" group
* Enable MFA for the root user
* Apply an IAM password policy that follows security best practices

### You need to answer the following: 

## What is Identity and Access Management (IAM)?

**Identity and Access Management (IAM)** is an AWS service that allows you to manage access to AWS resources securely. IAM enables you to create and manage AWS users, groups, roles, and policies, controlling who can access your AWS resources and what actions they can perform. IAM ensures that only authorized users and services have the permissions necessary to interact with AWS services and resources.

## What is a root user?

The **root user** is the account created when you first set up your AWS account. It has unrestricted access to all AWS services and resources within the account, including the ability to manage IAM users, billing, and account settings. The root user should be used sparingly due to its high level of privileges.

## How is a root user different from an Admin user?

- **Root User**:
  - **Full Access**: Has unrestricted access to all AWS services and resources.
  - **Account Management**: Can manage all aspects of the AWS account, including IAM, billing, and support settings.
  - **Security Risk**: High risk if compromised; should be used only for account-level tasks.

- **Admin User**:
  - **Limited Scope**: Typically has administrative access to manage resources and services but does not have unrestricted access to account-level settings.
  - **Custom Permissions**: Admin users are created with specific IAM policies that grant broad access to AWS resources but do not include account management features.
  - **Security Best Practice**: Use admin users for daily management tasks to limit the use of the root user.

## What is console access and programmatic access?

- **Console Access**: Refers to accessing AWS services through the AWS Management Console, a web-based graphical user interface. Users log in using their credentials and interact with AWS services via a web browser.

- **Programmatic Access**: Refers to accessing AWS services via APIs, CLI (Command Line Interface), or SDKs (Software Development Kits). Users use access keys (access key ID and secret access key) to authenticate and authorize requests made through these tools.

## What is the access key and secret key?

- **Access Key**: An identifier used to authenticate programmatic requests to AWS services. It consists of an **access key ID** and a **secret access key**.
- **Secret Key**: A cryptographic key used in conjunction with the access key ID to sign requests. The secret key is never shared and should be kept confidential.

## What is MFA and why is it important?

**Multi-Factor Authentication (MFA)** is a security feature that adds an additional layer of protection to your AWS account. It requires users to provide a second form of authentication (e.g., a code from a hardware token or mobile app) in addition to their password. MFA is important because it enhances security by reducing the risk of unauthorized access due to compromised passwords.

## What are policies and how can you create them?

**Policies** are JSON documents that define permissions for AWS users, groups, or roles. They specify what actions are allowed or denied on AWS resources. Policies can be attached to users, groups, or roles to control access.

- **Creating Policies**:
  - **AWS Management Console**: Use the IAM console to create and manage policies.
  - **AWS CLI/SDK**: Use commands or API calls to create policies programmatically.
  - **JSON**: Define policies in JSON format, specifying actions, resources, and conditions.

## What are roles and how can you create them?

**Roles** are AWS IAM entities that define a set of permissions and can be assumed by AWS services, users, or applications. Roles provide temporary security credentials to entities that need access to AWS resources.

- **Creating Roles**:
  - **AWS Management Console**: Use the IAM console to create roles and specify trusted entities and permissions.
  - **AWS CLI/SDK**: Create roles programmatically using commands or API calls.
  - **Policies**: Attach policies to roles to grant the necessary permissions.

## What is the difference between a role and a policy?

- **Role**:
  - **Entity**: An IAM role is an entity that defines a set of permissions.
  - **Assumable**: Roles can be assumed by users, services, or applications to gain temporary access to resources.
  - **Trust Relationships**: Roles include trust policies that define who can assume the role.

- **Policy**:
  - **Document**: A policy is a JSON document that specifies permissions.
  - **Attached**: Policies are attached to users, groups, or roles to define what actions are allowed or denied.
  - **Permissions**: Policies contain statements specifying actions, resources, and conditions.

## What is a user group?

**User Groups** are collections of IAM users. Groups simplify permission management by allowing you to apply policies to multiple users at once. When a user is added to a group, they inherit the permissions associated with that group.

## What are some good security practices for password policies?

Good security practices for password policies include:
- **Length and Complexity**: Require passwords to be a minimum length (e.g., at least 12 characters) and include a mix of uppercase letters, lowercase letters, numbers, and special characters.
- **Regular Rotation**: Enforce regular password changes, such as every 60 or 90 days.
- **Password History**: Prevent users from reusing recent passwords by maintaining a history of previous passwords.
- **Lockout Mechanism**: Implement account lockout mechanisms after a certain number of failed login attempts to protect against brute force attacks.
- **MFA**: Require multi-factor authentication (MFA) to add an additional layer of security.

## References

* [Creating Your First IAM Admin User and Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html)
* [Security Best Practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
* [Root user in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)
* [Setting an IAM password policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html?icmpid=docs_iam_console)
* [IAM Policy examples](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_examples.html)
* [About IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)


## Tips
* Managed policies are created and maintained by AWS. A managed policy has a small, orange box on the left side of the policy's name.
* Use the [Google Authenticator](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) app for MFA.
* Do not ever commit, add or push any of your access and secret keys to source control systems like git. You must also never share or make your access keys public in any way shape or form. If you accidentaly have done so, make sure to delete the access and secret keys immediately in your console and generate new ones.
* By default, IAM users are not allowed access to the Billing console. It has to be enabled seperately by using the root user under "My Account".

## Output 
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/fb3fa9379490eecf759fed2fb30d5a7c39ff1498/Level%20100/12.%20Create%20an%20IAM%20user/IAM.png)
