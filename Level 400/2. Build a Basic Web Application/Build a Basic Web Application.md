## **Introduction**

This project demonstrates the creation of a full-stack web application using AWS Amplify, featuring a React frontend with user authentication, a serverless function for user sign-ups, and DynamoDB for data storage. AWS Amplify’s managed services make it easy to build a scalable and secure web application with seamless backend integration.

## **Why AWS Amplify?**

AWS Amplify provides backend services like hosting, authentication, and data storage, allowing developers to focus on application functionality without managing infrastructure.

## **Learning Outcomes**

- **Hosting**: Deploy a React app on AWS’s global CDN.
- **Authentication**: Enable user sign-in and sign-out.
- **Database Integration**: Use a real-time API and DynamoDB.
- **Function Execution**: Trigger Lambda functions on user sign-up.

## **Tech Stack**

- **AWS Amplify**: Hosting and backend services.
- **AWS AppSync**: Real-time API management.
- **AWS Lambda**: Serverless function for user data.
- **Amazon DynamoDB**: NoSQL database for storing user emails.
- **React**: Frontend framework.
- **Node.js & npm**: For dependencies.
- **Git & GitHub**: Version control.

## **Prerequisites**

- Familiarity with AWS services like Amplify, Lambda, and DynamoDB.
- AWS CLI configured with appropriate IAM permissions.
- Node.js, npm, and Git installed locally.

## Problem Statement or Use Case

Web applications today require features like user authentication, data storage, and API integration. Setting up and managing these services can be challenging, especially for scalability and real-time capabilities. Using AWS Amplify simplifies this by offering a fully managed backend that integrates seamlessly with the frontend.

**Solution**: This project provides a user sign-up and sign-in system with a backend that captures and stores user data. This setup is applicable to various real-world scenarios, from building social media platforms to e-commerce websites, where user management and data storage are essential.

## Architecture Diagram

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4mayct551eo575aydeai.gif)

## Step-by-Step Implementation

### Tasks

This project is structured into six main tasks:

1. **Create Web App**: Deploy a React app using AWS Amplify Console.
2. **Build Serverless Function**: Create a Lambda function.
3. **Create Data Table**: Set up DynamoDB for data persistence.
4. **Link Function to Web App**: Deploy function with API Gateway.
5. **Add Web App Interactivity**: Update the frontend to call the API.
6. **Clean Up Resources**: Delete resources to avoid charges.

### Task 1: Create a Web App

#### Overview

AWS Amplify offers a Git-based CI/CD workflow for building, deploying, and hosting single-page web applications or static sites with backends. When connected to a Git repository, Amplify determines the build settings for both the frontend framework and any configured backend resources and automatically deploys updates with every code commit.

In this task, you will start by creating a new React application and pushing it to a GitHub repository. You will then connect the repository to AWS Amplify web hosting and deploy it to a globally available content delivery network (CDN) hosted on an `amplifyapp.com` domain.

#### Key Concepts

- **React Application**: React is a JavaScript library that enables developers to quickly build performant single-page applications.
- **Git**: Git is a version control system that allows developers to store files, maintain and update relationships between files and directories, and track versions and changes to the files.

#### Implementation

**Step 1: Create a new React application**

In a new terminal or command line window, run the following command to use Vite to create a React application:

```bash
npm create vite@latest profilesapp -- --template react
cd profilesapp
npm install
npm run dev
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/t0sajmzc7a61mljsqrir.png)

2. In the terminal window, select and open the Local link to view the Vite + React application.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6y525csrkuh72haa1jx6.png)

**Step 2: Initialize a GitHub repository**

In this step, you will create a GitHub repository and commit your code to the repository. You will need a GitHub account to complete this step; if you do not have an account, sign up [here](https://github.com).


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/otjklt5uv01211kf834p.png)

**Note**: If you have never used GitHub on your computer, follow these steps before continuing to allow connection to your account.

1. Sign in to GitHub at [https://github.com/](https://github.com/).

2. In the "Start a new repository" section, make the following selections:
   - For **Repository name**, enter `profilesapp`, and choose the **Public** radio button.
   - Then select **Create a new repository**.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i6nzs3lk1zjenwzvgwxm.png)

3. Open a new terminal window, navigate to your project's root folder (`profilesapp`), and run the following commands to initialize Git and push the application to the new GitHub repository:

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<your-username>/profilesapp.git
git branch -M main
git push -u origin main
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/md9f3uyqd2cf25bccrr7.png)

**Step 3: Install the Amplify packages**

Open a new terminal window, navigate to your app's root folder (`profilesapp`), and run the following command:

```bash
npm create amplify@latest -y
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ffi0jc5ti2bja5msmndz.png)

2. Running the previous command will scaffold a lightweight Amplify project in the app’s directory.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dblt2ars8yvzz0agkr90.png)

3. In your terminal window, run the following command to push the changes to GitHub:

```bash
git add .
git commit -m 'installing amplify'
git push origin main
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x4to2iy2yxwyv9oc3o0s.png)

**Step 4: Deploy your app with AWS Amplify**

1. Sign in to the AWS Management console in a new browser window and open the AWS Amplify console at [https://console.aws.amazon.com/amplify/apps](https://console.aws.amazon.com/amplify/apps).

2. Choose **Create new app**.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o4unzvbc5c7nm9efbiqa.png)

3. On the **Start building with Amplify** page, for **Deploy your app**, select **GitHub**, and select **Next**.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c2bzvwlalcv5x6rxyb4u.png)

4. When prompted, authenticate with GitHub. You will be automatically redirected back to the Amplify console. Choose the repository and main branch you created earlier. Then select **Next**.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/g5st31c3chq1znygkb6m.png)

5. Leave the default build settings, and select **Next**.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5jp9b8uoe8v9y5v2z0zy.png)



6. Review the inputs selected, and choose **Save and deploy**.

AWS Amplify will now build your source code and deploy your app at `https://...amplifyapp.com`, and on every git push, your deployment instance will update. It may take up to 5 minutes to deploy your app.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sy7szb8d5w747v2g2l9p.png)



7. Once the build completes, select the **Visit deployed URL** button to see your web app up and running live.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ivoa8ehpozztkeypn5vm.png)

### Conclusion

You have deployed a React application in the AWS Cloud by integrating with GitHub and using AWS Amplify. With AWS Amplify, you can continuously deploy your application in the Cloud and host it on a globally available CDN.

### Task 2: Build a Serverless Function

#### Overview

Now that you have a React web app, you will use AWS Amplify and AWS Lambda to configure a serverless function. This function is invoked after a signed-up user confirms their user account. AWS Lambda is a compute service that runs your code in response to events and automatically manages the compute resources, making it the fastest way to turn an idea into modern, production, serverless applications.

#### Key Concepts

- **Serverless function**: A piece of code that will be executed by a compute service, on demand.

#### Implementation

**Step 1: Setup an Amplify Function**

1. On your local machine, navigate to the `profilesapp/amplify/auth` folder and create a new folder inside the `amplify/auth` folder, naming it `post-confirmation`, and then create the files named `resource.ts` and `handler.ts` inside the folder.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bogzj65o7wf99o9ukzrj.png)



2. Update the `amplify/auth/post-confirmation/resource.ts` file with the following code to define the `postConfirmation` function:

```typescript
import { defineFunction } from '@aws-amplify/backend';

export const postConfirmation = defineFunction({
  name: 'post-confirmation',
});
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fntkdnkcfsm2cfd5ne06.png)



3. Update the `amplify/auth/post-confirmation/handler.ts` file with the following code to define the function’s handler:

```typescript
import type { PostConfirmationTriggerHandler } from "aws-lambda";

export const handler: PostConfirmationTriggerHandler = async (event) => {
  return event;
};
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/d5ksi1juwym25ibt3z55.png)


#### Conclusion

You have defined a Lambda function using Amplify.

### Task 3: Create a Data Table

#### Overview

In this task, you will create a data model to persist data using a GraphQL API and Amazon DynamoDB. Additionally, you will use AWS Identity and Access Management (IAM) authorization to securely give our services the required permissions to interact with each other. You will also allow the Lambda function you created in the previous task to use the GraphQL API to write to your newly created DynamoDB table using an IAM policy.

#### Key Concepts

- **Amplify backend**: Amplify Gen 2 uses a full-stack TypeScript developer experience (DX) for defining backends. Simply author app requirements like data models, business logic, and auth rules in TypeScript. Amplify automatically configures the correct cloud resources and deploys them to per-developer cloud sandbox environments for fast, local iteration.

#### Implementation

**Step 1: Setup Amplify Data**

1. On your local machine, navigate to the `amplify/data/resource.ts` file and update it with the following code:

```typescript
import { type ClientSchema, a, defineData } from "@aws-amplify/backend";
import { postConfirmation } from "../auth/post-confirmation/resource";

const schema = a
  .schema({
    UserProfile: a
      .model({
        email: a.string(),
        profileOwner: a.string(),
      })
      .authorization((allow) => [
        allow.ownerDefinedIn("profileOwner"),
      ]),
  })
  .authorization((allow) => [allow.resource(postConfirmation)]);

export type Schema = ClientSchema<typeof schema>;

export const data = defineData({
  schema,
  authorizationModes: {
    defaultAuthorizationMode: "apiKey",
    apiKeyAuthorizationMode: {
      expiresInDays: 30,
    },
  },
});
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5scoyaeu1p227is9bcz0.png)


2. Open a new terminal window, navigate to your app's root folder (`profilesapp`), and run the following command to deploy cloud resources into an isolated development space:

```bash
npx ampx sandbox
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iphddrjfktza2sb6y7or.png)



3. Once the cloud sandbox has been fully deployed, your terminal will display a confirmation message, and the `amplify_outputs.json` file will be generated and added to your project.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xt0rpvaw5xi223okiwpl.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zbvyemi9fd4pmsf8a459.png)




4. Open a new terminal window, navigate to your app's root folder (`profilesapp`), and run the following command to generate the GraphQL client code to call your data backend:

```bash
npx ampx generate graphql-client-code --out <path-to-post-confirmation-handler-dir>/graphql
```

Amplify will create the folder `amplify/auth/post-confirmation/graphql`, where you will find the client code to connect to the GraphQL API.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/buff7yvjrcz18eg6j9zn.png)

**Step 2: Modify Lambda Function to Connect to the API**

1. On your local machine, navigate to the `amplify/auth/post-confirmation/handler.ts` file and replace the code with the following:

```typescript
import type { PostConfirmationTriggerHandler } from "aws-lambda";
import { type Schema } from "../../data/resource";
import { Amplify } from "aws-amplify";
import { generateClient } from "aws-amplify/data";
import { env } from "$amplify/env/post-confirmation";
import { createUserProfile } from "./graphql/mutations";

Amplify.configure(
  {
    API: {
      GraphQL: {
        endpoint: env.AMPLIFY_DATA_GRAPHQL_ENDPOINT,
        region: env.AWS_REGION,
        defaultAuthMode: "iam",
      },
    },
  },
  {
    Auth: {
      credentialsProvider: {
        getCredentialsAndIdentityId: async () => ({
          credentials: {
            accessKeyId: env.AWS_ACCESS_KEY_ID,
            secretAccessKey: env.AWS_SECRET_ACCESS_KEY,
            sessionToken: env.AWS_SESSION_TOKEN,
          },
        }),
        clearCredentialsAndIdentityId: () => {
          /* noop */
        },
      },
    },
  }
);

const client = generateClient<Schema>({
  authMode: "iam",
});

export const handler: PostConfirmationTriggerHandler = async (event) => {
  await client.graphql({
    query: createUserProfile,
    variables: {
      input: {
        email: event.request.userAttributes.email,
        profileOwner: `${event.request.userAttributes.sub}::${event.userName}`,
      },
    },
  });

  return event;
};
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wqvkgzsmmrte36lphzy4.png)


#### Conclusion

You have created a data table and configured a GraphQL API to persist data in an Amazon DynamoDB database. Then, you updated the Lambda function to use the API.

### Task 4: Link a Serverless Function to a Web App

#### Overview

In this task, you will update the Amplify Auth resources to use the Lambda function created in the previous module as an Amazon Cognito post-confirmation invocation. When the user completes the sign-up, the function will use the GraphQL API and capture the user’s email into the DynamoDB table.

#### Key Concepts

- **Lambda invocation**: The type of event that will make a Lambda (serverless) function run. This can be another AWS service or an external input.

#### Implementation

**Step 1: Setup Amplify Auth**

1. On your local machine, navigate to the `amplify/auth/resource.ts` file and update it with the following code:

```typescript
import { defineAuth } from '@aws-amplify/backend';
import { postConfirmation } from './post-confirmation/resource';

export const auth = defineAuth({
  loginWith: {
    email: true,
  },
  triggers: {
    postConfirmation
  }
});
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wvhc4cmh7yk2rygooc2l.png)


2. The sandbox will automatically get updated and redeployed once the file is updated. If the sandbox is not running, you can run the following command in a new terminal window:

```bash
npx ampx sandbox
```

3. Once the cloud sandbox has been fully deployed, your terminal will display a confirmation message, and the `amplify_outputs.json` file will be generated/updated and added to your `profilesapp` project.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9dwakgb67ot13p7ljfa8.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lk9y6p9dqssbatfahfqc.png)



#### Conclusion

You used Amplify to configure authentication and set up the Lambda function to be invoked when the user signs in to the app.

### Task 5: Add Interactivity to Your Web App

#### Overview

In this task, you will create a frontend for your app and connect it to the cloud backend you have already built. You will update the website to use the Amplify UI component library to scaffold out an entire user authentication flow, allowing users to sign up, sign in, reset their password, and invoke the GraphQL API.

#### Key Concepts

- **Amplify libraries**: The Amplify libraries allow you to interact with AWS services from a web or mobile application.

#### Implementation

**Step 1: Install the Amplify libraries**

In a new terminal window, in your project's root folder (`profilesapp`), run the following command:

```bash
npm install aws-amplify @aws-amplify/ui-react
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1b5f5ilu9vlb1xiabv7c.png)

**Step 2: Style the app UI**

On your local machine, navigate to the `profilesapp/src/index.css` file and update it with the following code:

```css
:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.87);
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
}

.card {
  padding: 2em;
}

.read-the-docs {
  color: #888;
}

.box:nth-child(3n + 1) {
  grid-column: 1;
}
.box:nth-child(3n + 2) {
  grid-column: 2;
}
.box:nth-child(3n + 3) {
  grid-column: 3;
}
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9kow792o60t4igvm2m5e.png)


**Step 3: Implement the UI**

On your local machine, navigate to the `profilesapp/src/main.jsx` file and update it with the following code:

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";
import { Authenticator } from "@aws-amplify/ui-react";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <Authenticator>
      <App />
    </Authenticator>
  </React.StrictMode>
);
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ai18bnuhs676tdpzgqd4.png)


2. Open the `profilesapp/src/App.jsx` file and update it with the following code:

```javascript
import { useState, useEffect } from "react";
import {
  Button,
  Heading,
  Flex,
  View,
  Grid,
  Divider,
} from "@aws-amplify/ui-react";
import { useAuthenticator } from "@aws-amplify

/ui-react";
import { Amplify } from "aws-amplify";
import "@aws-amplify/ui-react/styles.css";
import { generateClient } from "aws-amplify/data";
import outputs from "../amplify_outputs.json";

Amplify.configure(outputs);
const client = generateClient({
  authMode: "userPool",
});

export default function App() {
  const [userprofiles, setUserProfiles] = useState([]);
  const { signOut } = useAuthenticator((context) => [context.user]);

  useEffect(() => {
    fetchUserProfile();
  }, []);

  async function fetchUserProfile() {
    const { data: profiles } = await client.models.UserProfile.list();
    setUserProfiles(profiles);
  }

  return (
    <Flex
      className="App"
      justifyContent="center"
      alignItems="center"
      direction="column"
      width="70%"
      margin="0 auto"
    >
      <Heading level={1}>My Profile</Heading>

      <Divider />

      <Grid
        margin="3rem 0"
        autoFlow="column"
        justifyContent="center"
        gap="2rem"
        alignContent="center"
      >
        {userprofiles.map((userprofile) => (
          <Flex
            key={userprofile.id || userprofile.email}
            direction="column"
            justifyContent="center"
            alignItems="center"
            gap="2rem"
            border="1px solid #ccc"
            padding="2rem"
            borderRadius="5%"
            className="box"
          >
            <View>
              <Heading level="3">{userprofile.email}</Heading>
            </View>
          </Flex>
        ))}
      </Grid>
      <Button onClick={signOut}>Sign Out</Button>
    </Flex>
  );
}
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jkoqohy8ztbz27g7n8vw.png)


**Step 4: Run the Application**

1. Open a new terminal window, navigate to your project's root directory (`profilesapp`), and run the following command to launch the app:

```bash
npm run dev
```

2. Select the Local host link to open the Vite + React application.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mvff8jvy5nrij2za9oi6.png)


3. Choose the **Create Account** tab and use the authentication flow to create a new user by entering your email address and a password. Then, choose **Create Account**.

4. You will receive a verification code sent to your email. Enter the verification code to log in to the app. When signed in, the app will display your email address.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/inraqyvmrtxy2kxmjvtj.png)


5. In the open terminal window, run the following command to push the changes to GitHub:

```bash
git add .
git commit -m 'displaying user profile'
git push origin main
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zh8dhlofgb6iw2osax8h.png)


6. Sign in to the AWS Management console in a new browser window, and open the AWS Amplify console at [https://console.aws.amazon.com/amplify/apps](https://console.aws.amazon.com/amplify/apps).

7. AWS Amplify automatically builds your source code and deploys your app at `https://...amplifyapp.com`. Select the **Visit deployed URL** button to see your web app up and running live.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h7okpx5dhndnrchgravv.png)


#### Conclusion

You have successfully added interactivity to your web app, allowing users to sign up, log in, and view their profiles using AWS Amplify’s powerful UI components.

### Task 6: Clean Up Resources

#### Overview

To finish this tutorial, you will clean up the resources created throughout. It is a best practice to delete resources you are no longer using to avoid unwanted charges.

#### Implementation

1. In the Amplify console, in the left-hand navigation for the `profilesapp`, choose **App settings** and select **General settings**.
2. In the General settings section, choose **Delete app**.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6ej3dr5h0pe1fqypus1r.png)

## Closure

This project provided valuable experience in creating a web application with user authentication and data storage using AWS Amplify. This serverless application setup is ideal for rapid development and scalability, making it suitable for various applications, from prototypes to production-level solutions. AWS Amplify enables efficient web application management and backend integration, covering a range of use cases.

Explore my [GitHub repository.](https://github.com/shubhammurti/AWS-Projects-Portfolio/)

> **Shubham Murti — Aspiring Cloud Security Engineer | Weekly Cloud Learning !!**

**Let’s connect:** [Linkdin](http://www.linkedin.com/in/shubham-murti-b6486a1aa), [Twitter](https://x.com/murti_shubham), [Github](https://github.com/shubhammurti)
