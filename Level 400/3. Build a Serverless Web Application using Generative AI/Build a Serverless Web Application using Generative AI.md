## **Introduction**

This project walks through creating a serverless recipe generator application using AWS Amplify and Amazon Bedrock. Users can input ingredients and receive AI-generated recipes via a simple web interface. By combining Generative AI with a serverless architecture, this application offers a scalable and interactive experience.

## **Tech Stack**

- **AWS Amplify**: Provides full-stack hosting and deployment services for the application.
- **Amazon Bedrock**: Utilized as an AI model to generate recipes based on user input.
- **AWS AppSync**: Manages real-time API connections between the frontend and backend.
- **AWS Cognito**: Provides secure user authentication.
- **AWS Lambda**: Handles serverless backend functionality for processing requests.
- **Node.js, npm, Git, GitHub**: Essential tools for frontend dependencies and version control.

## **Prerequisites**

- AWS Account: Permissions for Amplify, Cognito, Bedrock, and Lambda.
- AWS CLI and Amplify CLI: For resource management.
- Node.js & npm: For running React app.
- GitHub: Enables Amplify’s continuous deployment.

#### **Use Case**

**Problem**: Searching for suitable recipes based on available ingredients can be time-consuming, and manually sifting through results often yields non-personalized options.

**Solution**: This serverless recipe generator offers a **real-time AI-powered solution**, allowing users to input ingredients and receive tailored recipes instantly. The use of **Amazon Bedrock** makes it possible to generate diverse, personalized recipes on demand, saving users time and enhancing their cooking experience.

**Real-World Relevance**: This type of application has potential in e-commerce, cooking platforms, and smart home solutions. By integrating **Generative AI** and **serverless architecture**, we demonstrate a scalable, real-time solution for creating personalized recipes or content.

---

#### **Architecture Diagram**

![Architecture Diagram](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ppdfoxymhxa27bw6zfki.gif)

To follow along with this tutorial, you will need:

- **AWS Account**: Requires permissions for Amplify, Cognito, Bedrock, and Lambda.
- **AWS CLI**: Needed for resource management.
- **Node.js & npm**: For running the React app.
- **Amplify CLI**: For initializing and configuring the Amplify project.
- **Basic AWS Knowledge**: Familiarity with Amplify, Cognito, AppSync, and Lambda services.
- **GitHub Repository**: To enable Amplify’s continuous deployment integration.

---

#### **Component Breakdown**

1. **Frontend (React Application)**:  
   User-facing interface where users input ingredients and receive generated recipes. Hosted on **AWS Amplify** with continuous deployment.

2. **AWS Cognito**:  
   Manages secure authentication for users, ensuring only authorized access to backend resources.

3. **AWS AppSync**:  
   Provides the GraphQL API to handle communication between the frontend and backend services.

4. **AWS Lambda**:  
   Serverless function that takes user input and forwards it to **Amazon Bedrock** for AI-powered recipe generation.

5. **Amazon Bedrock (Claude 3 Sonnet)**:  
   Utilizes generative AI to create unique recipes based on input ingredients.

---

### **Step-by-Step Implementation**

---

#### **Task 1: Host a Static Website**

In this task, you will create a React application and deploy it to the Cloud using **AWS Amplify**.

---

**Step 1: Create a New React Application**

1. In a new terminal or command line window, run the following command to use Vite to create a React application:

   ```bash
   npm create vite@latest ai-recipe-generator -- --template react-ts -y
   ```

2. Navigate to the project directory:

   ```bash
   cd ai-recipe-generator
   ```

3. Install the necessary dependencies:

   ```bash
   npm install
   ```

4. Start the development server:

   ```bash
   npm run dev
   ```

   This will start your React application locally. You should see the Vite + React app running.

   ![React App](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o3cg5232jkrcbdjh4i1i.png)

5. In the terminal window, open the local link to view the application.

   ![Local Link](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7qj1cejzg9rr5kif8y4m.png)

---

**Step 2: Initialize a GitHub Repository**

In this step, you will create a GitHub repository and commit your code to it.

1. Sign in to GitHub at [GitHub](https://github.com/).
   
2. Create a new repository:
   - For **Repository name**, enter `ai-recipe-generator`.
   - Choose the **Public** radio button.
   - Select **Create a new repository**.

3. Open a new terminal window, navigate to your project’s root folder (`ai-recipe-generator`), and run the following commands to initialize Git and push the application to your GitHub repository:

   ```bash
   git init
   git add .
   git commit -m "first commit"
   git remote add origin git@github.com:<your-username>/ai-recipe-generator.git
   git branch -M main
   git push -u origin main
   ```

   Replace the `git@github.com:<your-username>/ai-recipe-generator.git` with your own GitHub SSH URL.

   ![GitHub Commit](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bzy6481oamgjn8vavj0z.png)

---

**Step 3: Install the Amplify Packages**

1. Open a new terminal window, navigate to your app's root folder (`ai-recipe-generator`), and run the following command:

   ```bash
   npm create amplify@latest -y
   ```

   This will scaffold a lightweight Amplify project in your app’s directory.

2. After installation, push the changes to GitHub:

   ```bash
   git add .
   git commit -m 'installing amplify'
   git push origin main
   ```

   ![Amplify Install](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ja94euu0euwt1khbnmsh.png)

---

**Step 4: Deploy Your App with AWS Amplify**

1. Sign in to the **AWS Management Console** and open the **AWS Amplify** console at [AWS Amplify](https://console.aws.amazon.com/amplify/apps).

2. Click **Create new app**.

3. On the **Start building with Amplify** page, select **GitHub** for **Deploy your app** and click **Next**.

4. Authenticate with GitHub. You will be automatically redirected back to the Amplify console. Choose the repository and main branch you created earlier, then select **Next**.

5. Leave the default build settings and click **Next**.

6. Review your inputs and click **Save and deploy**.

   AWS Amplify will now build your source code and deploy your app at `https://...amplifyapp.com`. Your app will automatically update with every Git push. It may take up to 5 minutes to deploy.

7. Once the build is complete, click **Visit deployed URL** to see your web app live.

---

#### **Task 2: Manage Users**

In this task, you will configure **Amplify Auth** for user authentication and enable **Amazon Bedrock** foundation model access.

---

**Step 1: Set up Amplify Auth**

1. The app uses email as the default login mechanism. When users sign up, they will receive a verification email. Customize the verification email by updating the following code in the `ai-generated-recipes/amplify/auth/resource.ts` file:

   ```ts
   import { defineAuth } from "@aws-amplify/backend";

   export const auth = defineAuth({
     loginWith: {
       email: {
         verificationEmailStyle: "CODE",
         verificationEmailSubject: "Welcome to the AI-Powered Recipe Generator!",
         verificationEmailBody: (createCode) =>
           `Use this code to confirm your account: ${createCode()}`,
       },
     },
   });
   ```

   Save the file.

   ![Custom Verification Email](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8nkluiubpy8qm052hxpv.png)

   The image on the right shows an example of the customized verification email.

---

**Step 2: Set up Amazon Bedrock Model Access**

1. Sign in to the **AWS Management Console** and open the **Amazon Bedrock** console at [AWS Amazon Bedrock](https://console.aws.amazon.com/bedrock/).

   Verify that you are in the **N. Virginia (us-east-1)** region, and select **Get started**.

2. In the **Foundation models** section, choose the **Claude model**.

3. Scroll down to the **Claude models** section, select the **Claude 3 Sonnet** tab, and click **Request model access**.

   - If you already have access to some models, the button will show **Manage model access** instead.

4. In the **Base models** section, for **Claude 3 Sonnet**, choose **Available to request**, then select **Request model access**.

5. On the **Edit model access** page, click **Next**.

6. On the **Review and Submit** page, click **Submit**.

---

Now your application should be up and running, with user authentication and AI-powered recipe generation using **Amazon Bedrock**'s **Claude 3 Sonnet**.

Here's the reformatted version of **Task 3: Build a Serverless Backend** and **Task 4: Deploy the Backend API**, with improved structure and readability for a Medium blog post:

---

### **Task 3: Build a Serverless Backend**

In this task, you will use **AWS Amplify** and **AWS Lambda** to build a serverless function.

---

#### **Step 1: Create a Lambda Function for Handling Requests**

1. On your local machine, navigate to the `ai-recipe-generator/amplify/data` folder, and create a new file named `bedrock.js`.

2. Update the file with the following code:

   The code defines a request function that constructs the HTTP request to invoke the **Claude 3 Sonnet** foundation model in **Amazon Bedrock**. The response function parses the response and returns the generated recipe.

   ```js
   export function request(ctx) {
     const { ingredients = [] } = ctx.args;
   
     // Construct the prompt with the provided ingredients
     const prompt = `Suggest a recipe idea using these ingredients: ${ingredients.join(", ")}.`;
   
     // Return the request configuration
     return {
       resourcePath: `/model/anthropic.claude-3-sonnet-20240229-v1:0/invoke`,
       method: "POST",
       params: {
         headers: {
           "Content-Type": "application/json",
         },
         body: JSON.stringify({
           anthropic_version: "bedrock-2023-05-31",
           max_tokens: 1000,
           messages: [
             {
               role: "user",
               content: [
                 {
                   type: "text",
                   text: `\n\nHuman: ${prompt}\n\nAssistant:`,
                 },
               ],
             },
           ],
         }),
       },
     };
   }
   
   export function response(ctx) {
     // Parse the response body
     const parsedBody = JSON.parse(ctx.result.body);
   
     // Extract the text content from the response
     const res = {
       body: parsedBody.content[0].text,
     };
   
     // Return the response
     return res;
   }
   ```

   The `request` function constructs the AI prompt and sends it to Amazon Bedrock. The `response` function parses the generated recipe from the returned JSON.

---

#### **Step 2: Add Amazon Bedrock as a Data Source**

1. Open the `amplify/backend.ts` file and add the following code. Save the file.

   The code adds an HTTP data source for **Amazon Bedrock** to your API and grants it the necessary permissions to invoke the Claude model.

   ```ts
   import { defineBackend } from "@aws-amplify/backend";
   import { data } from "./data/resource";
   import { PolicyStatement } from "aws-cdk-lib/aws-iam";
   import { auth } from "./auth/resource";

   const backend = defineBackend({
     auth,
     data,
   });

   const bedrockDataSource = backend.data.resources.graphqlApi.addHttpDataSource(
     "bedrockDS",
     "https://bedrock-runtime.us-east-1.amazonaws.com",
     {
       authorizationConfig: {
         signingRegion: "us-east-1",
         signingServiceName: "bedrock",
       },
     }
   );

   bedrockDataSource.grantPrincipal.addToPrincipalPolicy(
     new PolicyStatement({
       resources: [
         "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0",
       ],
       actions: ["bedrock:InvokeModel"],
     })
   );
   ```

   This code integrates Amazon Bedrock into your backend, enabling the serverless app to invoke the Claude 3 Sonnet model.

---

### **Task 4: Deploy the Backend API**

#### **Step 1: Set Up Amplify Data**

1. In the `amplify/backend.ts` file, define the schema and backend resources as follows:

   ```ts
   import { type ClientSchema, a, defineData } from "@aws-amplify/backend";

   const schema = a.schema({
     BedrockResponse: a.customType({
       body: a.string(),
       error: a.string(),
     }),

     askBedrock: a
       .query()
       .arguments({ ingredients: a.string().array() })
       .returns(a.ref("BedrockResponse"))
       .authorization((allow) => [allow.authenticated()])
       .handler(
         a.handler.custom({ entry: "./bedrock.js", dataSource: "bedrockDS" })
       ),
   });

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

   In this step, you define a **GraphQL** schema and link the `askBedrock` query to the custom Lambda function you created earlier (`bedrock.js`). The schema allows authenticated users to invoke the function and retrieve a recipe suggestion.

   ![Amplify Schema](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rs3tc08p2l8eoz8bdqmv.png)

---

#### **Step 2: Deploy Cloud Resources**

1. Open a new terminal window, navigate to your app's project folder (`ai-recipe-generator`), and run the following command to deploy cloud resources into an isolated development space:

   ```bash
   npx ampx sandbox
   ```

   This command sets up a sandbox environment where you can quickly iterate on your changes.

   ![Sandbox Deployment](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c4qv9mmq04j2rubgtdsh.png)

2. After the sandbox has been fully deployed, you will see a confirmation message in the terminal, and an `amplify_outputs.json` file will be generated and added to your project.

   ![Deployment Confirmation](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nngqeowg8yujnrghraqx.png)

   The deployment process is now complete, and you can begin interacting with your serverless backend.

   ![Deployment Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dxs5y4th00wcuusq0jt1.png)

---

The serverless backend is now set up and ready to handle recipe generation requests using **Amazon Bedrock**. You've created a Lambda function to handle interactions with the Claude 3 Sonnet model, integrated it with AWS Amplify, and deployed it to the cloud.

Here's how you can present **Task 5: Build the Frontend** and the challenges faced in the process for your blog:

---

### **Task 5: Build the Frontend**

Now that the serverless backend is set up, it's time to create the frontend. This step will guide you through building the user interface (UI) using **AWS Amplify** libraries, styled components, and React. We’ll also implement authentication to ensure that only authorized users can access the app.

---

#### **Step 1: Install the Amplify Libraries**

To get started with integrating AWS Amplify into your frontend, you'll need to install the core Amplify libraries. The `aws-amplify` library provides all the necessary APIs to interact with your backend, while `@aws-amplify/ui-react` contains pre-built UI components that help you scaffold the authentication flow and other UI elements.

1. Open a new terminal window, navigate to your project’s root folder (`ai-recipe-generator`), and run the following command to install the libraries:

   ```bash
   npm install aws-amplify @aws-amplify/ui-react
   ```

   ![Install Amplify](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/d176go3ct67bdigeb6o3.png)

---

#### **Step 2: Style the App UI**

Next, we’ll style the frontend to create a clean, modern interface. We'll focus on centering the layout and styling the form where users will input their ingredients.

1. Open `ai-recipe-generator/src/index.css`, and update it with the following code to set global styles and center the UI:

   ```css
   :root {
     font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
     line-height: 1.5;
     font-weight: 400;
     color: rgba(255, 255, 255, 0.87);
     max-width: 1280px;
     margin: 0 auto;
     padding: 2rem;
   }

   .card {
     padding: 2em;
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

   This CSS will help ensure that the app's layout is centered, the font is legible, and the UI components have a clean, consistent style.

   ![CSS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ieqh5uzxrmiva5x1x9dc.png)

2. Next, open `ai-recipe-generator/src/App.css` and update it with the following code to style the ingredient input form:

   ```css
   .app-container {
     margin: 0 auto;
     padding: 20px;
     text-align: center;
   }

   .header-container {
     padding-bottom: 2.5rem;
     text-align: center;
   }

   .main-header {
     font-size: 2.25rem;
     font-weight: bold;
     color: #1a202c;
   }

   .main-header .highlight {
     color: #2563eb;
   }

   .description {
     font-weight: 500;
     font-size: 1.125rem;
     max-width: 65ch;
     color: #1a202c;
   }

   .form-container {
     margin-bottom: 20px;
   }

   .search-container {
     display: flex;
     flex-direction: column;
     gap: 10px;
     align-items: center;
   }

   .wide-input {
     width: 100%;
     padding: 10px;
     font-size: 16px;
     border: 1px solid #ccc;
     border-radius: 4px;
   }

   .search-button {
     width: 100%;
     max-width: 300px;
     padding: 10px;
     font-size: 16px;
     background-color: #007bff;
     color: white;
     border: none;
     border-radius: 4px;
     cursor: pointer;
   }

   .search-button:hover {
     background-color: #0056b3;
   }

   .result-container {
     margin-top: 20px;
     transition: height 0.3s ease-out;
     overflow: hidden;
   }

   .loader-container {
     display: flex;
     flex-direction: column;
     align-items: center;
     gap: 10px;
   }

   .result {
     background-color: #f8f9fa;
     border: 1px solid #e9ecef;
     border-radius: 4px;
     padding: 15px;
     white-space: pre-wrap;
     word-wrap: break-word;
     color: black;
     font-weight: bold;
     text-align: left;
   }
   ```

   This will ensure that the ingredients form and result display are properly styled.

   ![Form Styles](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pjcna5yvnsucsp74in5b.png)

---

#### **Step 3: Implement the UI**

Now, let’s build the main React component for the app. We’ll integrate the **AWS Amplify Authentication** components for user sign-up, sign-in, and password recovery.

1. Open `ai-recipe-generator/src/main.tsx` and update it with the following code. This will use the Amplify `Authenticator` component to wrap your app and provide a complete authentication flow:

   ```tsx
   import React from "react";
   import ReactDOM from "react-dom/client";
   import App from "./App.jsx";
   import "./index.css";
   import { Authenticator } from "@aws-amplify/ui-react";

   ReactDOM.createRoot(document.getElementById("root")!).render(
     <React.StrictMode>
       <Authenticator>
         <App />
       </Authenticator>
     </React.StrictMode>
   );
   ```

   The `Authenticator` component will handle user authentication, including sign-up, sign-in, and MFA (Multi-Factor Authentication).

   ![Authenticator](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dlc5kkyu52xhakwlcx0s.png)

2. Next, open `ai-recipe-generator/src/App.tsx` and update it with the following code to implement the form for ingredient submission and the logic for querying the **askBedrock** function.

   ```tsx
   import { FormEvent, useState } from "react";
   import { Loader, Placeholder } from "@aws-amplify/ui-react";
   import "./App.css";
   import { Amplify } from "aws-amplify";
   import { Schema } from "../amplify/data/resource";
   import { generateClient } from "aws-amplify/data";
   import outputs from "../amplify_outputs.json";

   import "@aws-amplify/ui-react/styles.css";

   Amplify.configure(outputs);

   const amplifyClient = generateClient<Schema>({
     authMode: "userPool",
   });

   function App() {
     const [result, setResult] = useState<string>("");
     const [loading, setLoading] = useState(false);

     const onSubmit = async (event: FormEvent<HTMLFormElement>) => {
       event.preventDefault();
       setLoading(true);

       try {
         const formData = new FormData(event.currentTarget);
         
         const { data, errors } = await amplifyClient.queries.askBedrock({
           ingredients: [formData.get("ingredients")?.toString() || ""],
         });

         if (!errors) {
           setResult(data?.body || "No data returned");
         } else {
           console.log(errors);
         }
       } catch (e) {
         alert(`An error occurred: ${e}`);
       } finally {
         setLoading(false);
       }
     };

     return (
       <div className="app-container">
         <div className="header-container">
           <h1 className="main-header">
             Meet Your Personal
             <br />
             <span className="highlight">Recipe AI</span>
           </h1>
           <p className="description">
             Simply type a few ingredients using the format ingredient1,
             ingredient2, etc., and Recipe AI will generate an all-new recipe on
             demand...
           </p>
         </div>
         <form onSubmit={onSubmit} className="form-container">
           <div className="search-container">
             <input
               type="text"
               className="wide-input"
               id="ingredients"
               name="ingredients"
               placeholder="Ingredient1, Ingredient2, Ingredient3,...etc"
             />
             <button type="submit" className="search-button">
               Generate
             </button>
           </div>
         </form>
         <div className="result-container">
           {loading ? (
             <div className="loader-container">
               <p>Loading...</p>
               <Loader size="large" />
               <Placeholder size="large" />
               <Placeholder size="large" />
               <Placeholder size="large" />
             </div>
           ) : (
             result && <p className="result">{result}</p>
           )}
         </div>
       </div>
     );
   }

   export default App;
   ```

   The app allows users to input a list of ingredients, submits the request to the backend via **Amplify** and **Amazon Bedrock**, and then displays the generated recipe.

   ![Recipe Generation UI](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oat3sk46j8c2f6svey5q.png)

---

#### **Step 4: Run and Test the App**

1. Open a new terminal window and navigate to your project’s root directory (`ai-recipe-generator`), then run:

   ```bash
   npm run dev
   ```

2. Visit the local host URL to open the app in your browser and test it.

---

#### **Step 5: Deploy the App**

Once you’ve confirmed that the app is working as expected locally, it’s time to deploy it to AWS Amplify.

1. In the terminal, commit your changes:

   ```bash
   git add .
   git commit -m 'connect to bedrock'
   git push origin main
   ```

2. Go to the **AWS Amplify** console, and your app should automatically build and deploy.

   After deployment, you can access your live app at the provided Amplify URL.

   ![Deployed App](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y3hki55r9i6tdwdid556.png)

---

## **Challenges and Solutions**

- **Handling Bedrock Latency**: Managed response delays with retry logic.
- **Real-Time Data Sync**: AppSync ensures consistent updates across all instances.

## **Conclusion**

This project combines AWS Amplify, Amazon Bedrock, and AWS Cognito to build a scalable, AI-powered recipe generator. It highlights the potential of serverless applications with Generative AI, making it ideal for real-time, interactive user experiences.

Explore my [GitHub repository.](https://github.com/shubhammurti/AWS-Projects-Portfolio/)

> **Shubham Murti — Aspiring Cloud Security Engineer | Weekly Cloud Learning !!**

**Let’s connect:** [Linkdin](http://www.linkedin.com/in/shubham-murti-b6486a1aa), [Twitter](https://x.com/murti_shubham), [Github](https://github.com/shubhammurti)
