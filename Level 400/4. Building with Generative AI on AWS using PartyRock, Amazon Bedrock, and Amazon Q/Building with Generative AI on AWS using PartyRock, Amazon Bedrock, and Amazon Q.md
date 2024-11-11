# Generative AI on AWS: PartyRock, Amazon Bedrock, and Amazon Titan

## **Introduction**

This project explores three distinct applications of **Generative AI on AWS** utilizing **PartyRock**, **Amazon Bedrock**, and **Amazon Titan**. Through practical experiments, we delve into no-code app development, advanced AI model integration, and retrieval-augmented generation (RAG) workflows. These projects demonstrate scalable AI solutions for various needs, from a book recommendation chatbot to context-aware response systems, all powered by AWS services.

## **Tech Stack**

- **PartyRock**: A no-code AI app builder with pre-configured widgets.
- **Amazon Bedrock**: Access to cutting-edge AI models, including:
  - **Claude 3 Sonnet**: For chat functionalities.
  - **Amazon Titan**: For text generation.
  - **Titan Image Generator**: Creates images based on prompts.
- **FAISS**: Enables similarity searches and vector storage for RAG.
- **Amazon Titan Text Embeddings**: Converts text to vectors for document-based AI models.

## **Prerequisites**

- **AWS Account**: Access to Bedrock, PartyRock, and Titan.
- **AWS CLI**: Used for configuration management.
- **Basic AWS Knowledge**: Familiarity with IAM roles, Bedrock, and AI model concepts.
- **No-Code Access**: PartyRock allows non-developers to build apps.

## **Use Case Overview**

This project highlights the potential of **Generative AI** in creating real-time content, context-aware responses, and AI-driven images. Here are three main applications:

1. **No-code Book Recommendation Chatbot**: Uses **PartyRock** to deliver personalized recommendations.
2. **Foundation Model Integration**: Powered by **Amazon Bedrock**, supporting real-time text, chat, and image generation.
3. **Retrieval-Augmented Generation (RAG)**: Combines **Amazon Titan**, **FAISS**, and **Claude 3 Sonnet** to provide accurate responses based on stored knowledge.

### **Industries Benefiting from AI-driven Solutions**
Industries such as customer service, e-commerce, and education can benefit significantly from these scalable and AI-driven applications.

### **Step-by-Step Implementation**

#### **Project 1: Build Generative AI Applications with PartyRock**

In this section, we’ll learn how to use **PartyRock** to generate AI apps without any code.

---

#### **What is PartyRock?**

**PartyRock** is a shareable Generative AI app-building playground that allows you to experiment with prompt engineering in a hands-on and fun way. In just a few clicks, you can build, share, and remix apps, getting inspired while playing with Generative AI. Some examples of what you can do with PartyRock include:

- Build an app to generate dad jokes on any topic of your choice.
- Create and play a virtual trivia game with friends around the world.
- Build an AI storyteller to guide your next fantasy roleplaying campaign.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/po3hqg0sdm6xvb974dq6.png)

By building and playing with PartyRock apps, you will learn the fundamental techniques and capabilities needed to get started with Generative AI. This includes understanding how a foundational model responds to prompts, experimenting with different text-based inputs, and chaining prompts together to create more dynamic outputs.

Anyone can experiment with PartyRock by creating a profile using a social login from **Amazon.com**, **Apple**, or **Google**. PartyRock is separate from the AWS console and does not require an AWS account to get started.

---

#### **Exercise 1: Building a PartyRock Application**

To highlight the power of PartyRock, we’re going to build an application that can provide book recommendations based on your mood.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6lnzdpigvc4ug3kyu5a3.png)



1. Head over to the **PartyRock website**.
2. Log in with a social account (Amazon, Apple, or Google).
3. Click on **Build your own app** and enter the following prompt: *"Provide book recommendations based on your mood and a chatbot to talk about the books."*
4. Click **Generate app**.

---

#### **Using the App**

PartyRock will create the interface needed to take in user input, provide recommendations, and create a chatbot—just from your prompt! Try the following:

- Enter a mood, like "Happy."
- Ask the chatbot for more information about the book recommendations by typing: *"Can you tell me more about one of the books that was listed?"*

You can also share your app by clicking the **Make public** and **Share** buttons.

---

#### **Updating Your App**

In PartyRock, each **UI element** is a *widget*, which displays content, takes input, connects to other widgets, and generates output. Widgets that take input allow users to interact with the app, while widgets that create output use prompts and references to generate something like an image or text.

---

##### **Types of Widgets**

There are three types of AI-powered widgets:

1. **Image Generation**
2. **Chatbot**
3. **Text Generation**

You can edit these widgets to connect them to others and change their outputs.

Additionally, there are three other widgets:

1. **User Input**: Allows users to change the output by connecting it to AI-powered widgets.
2. **Static Text**: Provides a space for text descriptions.
3. **Document Upload**: Lets users upload documents that can be processed by the app.

For more details, check out the [PartyRock Guide](#).

---

#### **Exercise 2: Playtime with PartyRock**

Now that you have a basic app, it’s time to explore! Try the following:

- Update the prompts in your app.
- Play with the settings.
- Chain outputs together to create new workflows.

Get creative and explore what PartyRock can do. For example, try adding a widget that can draw an image of the book based on its description.

---

#### **Remixing an Application**

With PartyRock, you can **Remix** applications, which lets you make a copy of an app and edit it to your liking. You can remix your own apps, or remix public apps from friends or from the PartyRock Discover page. 

Try remixing one of the apps from the Discover page to create new variations!

---

#### **Creating a Snapshot**

Did you get a funny or interesting response from an app you’re using? You can share a snapshot with others! Here's how:

1. Make sure the app is in **public mode**.
2. Click **Snapshot** in the top right corner of the app page.
3. The URL that includes the current input and output of your app will be copied to your clipboard, so you can share it with others.

---

#### **Wrap Up**

With **PartyRock**, you can demo and propose ideas that leverage **Generative AI** in a fun, easy-to-use environment. When you're ready to build apps for production, you can implement those ideas using **Amazon Bedrock**.

### **Project 2: Use Foundation Models in Amazon Bedrock**

**Amazon Bedrock** is a fully managed service that offers access to high-performing foundation models (FMs) from leading AI companies like Stability AI, Anthropic, and Meta, all via a single API. With Amazon Bedrock, you can securely integrate and deploy Generative AI capabilities into your applications, using the AWS services you’re already familiar with—without the need to manage infrastructure. 

In this module, we'll explore how to use **Amazon Bedrock** through the console and the API to generate both text and images.

---

#### **Model Access**

Before you can start building with Bedrock, you will need to grant model access to your AWS account.

1. Head to the **Model Access page**.
2. Select the **Enable specific models** button.
3. Check the models you wish to activate. If you're running this from your own account, there’s no cost to activate the models—you only pay for what you use during the labs. 

Here’s a list of supported models:

- **Amazon** (select to automatically activate all Amazon Titan models)
- **Anthropic**: Claude 3.5 Sonnet, Claude 3 Sonnet, Claude 3 Haiku
- **Meta**: Llama 3.1 405B Instruct, Llama 3.1 70B Instruct, Llama 3.1 8B Instruct
- **Mistral AI**
- **Stability AI**: SDXL 1.0

After selecting the models, click **Request model access** to activate them in your account.

![Model Access](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cm3one9auz1h68olk7xp.png)

---

#### **Monitor Model Access Status**

It may take a few minutes for the models to transition from "In Progress" to "Access granted" status. You can use the **Refresh** button to periodically check for updates.

Once the status shows **Access granted**, you're ready to begin.

![Access Granted](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7t6meg3v770ylq37kuzm.png)

---

#### **Using the Amazon Bedrock Playground**

The **Amazon Bedrock Playground** is a great way to experiment with different foundation models directly inside the AWS Console. You can compare model outputs, load example prompts, and even export API requests.

The playground currently supports three modes:

1. **Chat**: Experiment with a wide range of language processing tasks in a turn-by-turn interface.
2. **Text**: Test fast iterations on a variety of language processing tasks.
3. **Image**: Generate compelling images by providing text prompts to pre-trained models.

You can access the playground via the links above or from the **Amazon Bedrock Console** under the **Playgrounds** side menu. Take a few minutes to explore the examples.

---

#### **Playground Examples**

Here are some examples you can try in each playground mode:

##### **Chat Mode**

1. Click the **Select model** button to open the Model Selection popup.
2. Choose **Anthropic Claude 3 Sonnet**.
   
   ![Select Model](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0qg14ee3lfyrhv6213ci.png)
   
3. Click **Load examples** and select **Advanced Q&A with Citations**.
4. Once the example is loaded, click **Run** to start the chat.

   ![Advanced Q&A](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0rweqnq1i5a0ch9o3y0c.png)

You can adjust the model’s configuration in the sidebar. Try changing the **Temperature** to **1** to make the model more creative in its responses.

##### **Text Mode**

In this example, we selected **Amazon Titan Text G1 - Express** as the model and loaded the **JSON creation** example.

1. Try changing the model by selecting **Change** and choosing **Mistral** → **Mistral Large 2**.
2. Clear the output and run the prompt again.

   ![Text Mode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/83cls06zk61s3a228kuz.png)


Notice how the output differs. It's important to experiment with different foundation models to find the one that best fits your use case.

   ![Model Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ej5ox9evm9arrqabikdw.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s300d8c99k0h8vx689do.png)

##### **Image Mode**

1. Select **Titan Image Generator G1** as the model and load the **Generate images from a text prompt** example.

   ![Image Mode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s7lt1t8yg0b0e7zv1div.png)

2. Try changing the **Prompt Strength** to **10** and experiment with different prompts, such as:
   - *"Unicorns in a magical forest. Lots of trees and animals around. The mood is bright, and there is lots of natural lighting."*
   - *"Downtown City, with lots of skyscrapers. At night time, lots of lights in the buildings."*

Play around with different prompts to see how the model responds to variations in input.

## Expected Output
 - *"Unicorns in a magical forest. Lots of trees and animals around. The mood is bright, and there is lots of natural lighting."*
   
   ![image](https://github.com/user-attachments/assets/27830525-0d75-458f-a3b7-222b7b0ffd81)

- *"Downtown City, with lots of skyscrapers. At night time, lots of lights in the buildings."*
  
  ![image](https://github.com/user-attachments/assets/0369793b-d1fb-4968-b833-ed779381ec5f)

---

#### **Wrap Up: Using Amazon Bedrock in Applications via API**

Now that you’ve explored the Bedrock Playground, let’s see how we can bring the power of **Amazon Bedrock** to applications using the API.

The playground is a great starting point, but integrating these models into your applications will give you the flexibility to create production-level solutions. Whether you’re generating text, images, or handling interactive chat, Amazon Bedrock offers a serverless, scalable way to leverage powerful foundation models.

### Project 3: Chat with your Documents

This module teaches how to use **Retrieval Augmented Generation (RAG)**, a powerful approach that combines document retrieval with generative AI models to answer questions based on the content of documents. We'll learn how to set up a **RAG** system using Amazon Bedrock and work with various types of documents, including PDFs and knowledge bases, to generate accurate responses based on the context of the document.

#### **Architecture Overview**
In this module, the **Retrieval Augmented Generation (RAG)** system consists of several key components:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k57y319qgfpomugt5ykk.gif)

1. **Embeddings**: Text is converted into vector representations (embeddings) using models like Amazon Titan or Anthropic Claude. These embeddings capture the meaning and context of the text.
   
2. **Vector Database**: Once converted into embeddings, the text data is stored in a vector database, which enables quick and relevant retrieval of documents using similarity searches.

3. **Bedrock for RAG**: With embeddings and a vector store, we use Amazon Bedrock to retrieve the most relevant documents based on the user query and then pass those documents to a language model (like Claude or Titan) to generate a relevant answer.

4. **LangChain**: This Python framework simplifies the development of applications with LLMs and helps with managing the RAG process.

### **Exercise 1: Getting Started with RAG**

The `base_rag.py` script demonstrates how RAG works by using a small set of documents (sentences) and querying them to generate answers based on context.

1. **Document Setup**: Define a set of sentences representing different topics, such as pets, cities, and colors.

```python
sentences = [
    "Your dog is so cute.",
    "How cute your dog is!",
    "You have such a cute dog!",
    "New York City is the place where I work.",
    "I work in New York City.",
    "What color do you like the most?",
    "What is your favorite color?",
]
```

2. **Embedding with Amazon Bedrock**: Use the `Amazon Titan Text Embeddings` model to convert these sentences into embeddings.

```python
embeddings = BedrockEmbeddings(
    client=bedrock_runtime,
    model_id="amazon.titan-embed-text-v1",
)
```

3. **Vector Store with FAISS**: Store the embeddings in a **FAISS** vector store, which allows for efficient similarity searches.

```python
local_vector_store = FAISS.from_texts(sentences, embeddings)
```

4. **RAG Workflow**: Given a user query, convert the query into an embedding, retrieve the relevant documents, and combine the context of the documents to generate a coherent answer using a model like **Claude**.

```python
context = ""
for doc in docs:
    context += doc.page_content

prompt = f"""Use the following pieces of context to answer the question at the end.

{context}

Question: {query}
Answer:"""
```

5. **Run the Code**: Test the RAG system by running the script in the terminal.

```bash
python3 rag_examples/base_rag.py
```

You can experiment by modifying the query in the code. For instance, try asking, "What city do I work in?" and see how the system responds based on the context.

### **Exercise 2: Chat with a PDF**

Now let's work with a PDF document. In the file `chat_with_pdf.py`, the function `chunk_doc_to_text` will read the PDF and chunk its content into pieces, each of 1000 characters, before storing them in the vector database.

1. **PDF Chunking**: The process of chunking the document allows you to process large files and query sections of the document efficiently. 

2. **Querying the PDF**: After the PDF has been chunked, you can use a query like **"What are some good use cases for non-SQL databases?"** to test the retrieval and response capabilities.

Run the code as follows:

```bash
python3 rag_examples/chat_with_pdf.py
```

Play around with the queries and see how the model answers questions based on the PDF context.

### **Creating a Knowledge Base**

A Knowledge Base (KB) in Amazon Bedrock helps store and query documents in a structured manner. By uploading a dataset (e.g., AWS Well-Architected Framework) to Amazon S3, you can automatically create a KB, which will handle the embeddings and vector database setup.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yow0p9tsmrkmx31ajaav.png)



1. **Create Knowledge Base**: Navigate to the **Knowledge Base Console** and create a new Knowledge Base by uploading documents to an S3 bucket and selecting the embeddings model.

2. **Sync Data**: Once the Knowledge Base is created, click the **Sync** button to load the data. You can then query the KB for information like **"What is a VPC?"** and retrieve relevant responses.

3. **Query via Console**: Use the console to enter a query and see how the system responds. For example:

```text
Can you explain what a VPC is?
```
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/30s5ukr9bk33tyj8oli8.png)

### **Exercise 3: Using the Knowledge Base API**

You can also query your Knowledge Base programmatically via the API using the **retrieve** or **retrieve_and_generate** methods. These methods can be invoked to fetch documents or generate answers using the RAG process.

1. Open the file `kb_rag.py` and update the **KB_ID** with your created Knowledge Base ID.
2. Run the script using:

```bash
python3 rag_examples/kb_rag.py
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2ayc22s2uh1amn2khk4m.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fuat94bl9noci2aco821.png)

You can modify the `QUERY` variable to test different questions and see how the KB API performs.


### **Building Agents for Amazon Bedrock**

In this section, we'll build an **Agent** using Amazon Bedrock. An agent is a task-specific AI model that can interact with different services, such as querying Knowledge Bases or invoking AWS Lambda functions.

1. **Create an Agent**: In the **Agent Console**, create a new agent named `Agent-AWS`, select the model (Claude 3 Sonnet), and provide a role description (e.g., AWS Certified Solutions Architect).

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lf4pks9ndu8marleldk7.png)

2. **Define Action Groups**: Action groups are predefined tasks that the agent can perform. For instance, you can define an action to process data by reading records from a database.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/617rez9fm6sc8nfuqz7v.png)

3. **Knowledge Base Integration**: You can add the Knowledge Base you created earlier to the agent. This allows the agent to query the KB and use it to answer AWS-related questions.


4. **Test the Agent**: Once the agent is created, use the console to test it. Ask questions like **"What can you tell me about S3 buckets?"** and inspect the agent’s responses. You can also simulate errors to test the agent's capabilities to troubleshoot issues.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/07ksicatndz3onqfe3x8.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7db608roffuq95bwujau.png)


### **Debugging Lambda Functions with Amazon Q**
Use the following test event JSON to mimic the agent calling the fucntion
```JSON
{
  "agent": {
    "alias": "TSTALIASID",
    "name": "Agent-AWS",
    "version": "DRAFT",
    "id": "ADI6ICMMZZ"
  },
  "sessionId": "975786472213626",
  "httpMethod": "GET",
  "sessionAttributes": {},
  "inputText": "Can you get the number of records in the databse",
  "promptSessionAttributes": {},
  "apiPath": "/get_num_records",
  "messageVersion": "1.0",
  "actionGroup": "agent_action_group"
}
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w0n2fwkyfcoa4mw7ls62.png)

If you encounter errors in Lambda functions triggered by the agent, you can use **Amazon Q** to debug and resolve issues.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8eoe6berjku3fikc2nur.png)


1. **Invoke Lambda Function**: In the Lambda console, invoke your function and intentionally trigger an error.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/g8d27wb91zpguhbhvz8w.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l4dorvy7char0ob8j2pp.png)



2. **Troubleshoot with Amazon Q**: Use **Amazon Q** to debug the error and resolve issues by following the troubleshooting steps.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rv5jkl16jannyzw2on3n.png)


### **Clean-up**

Once you've finished, make sure to clean up your resources by deleting:

- **S3 Objects**: Delete any objects in the S3 buckets (e.g., `awsdocsbucket`, `openapiBucket`).
- **IAM Roles**: Delete IAM roles associated with Bedrock and other services.
- **Knowledge Base**: Delete the Knowledge Base and any related data.
- **Agent**: Delete the agent.
- **OpenSearch Collection**: Delete the vector store.
- **CloudFormation Stack**: Delete the CloudFormation stack to remove all resources.

### Conclusion

This project demonstrates the flexibility of Generative AI on AWS to build dynamic applications. Whether it’s no-code development with PartyRock, scalable AI integrations with Bedrock, or context-driven responses through RAG, AWS offers the tools to create efficient and powerful AI solutions. These applications highlight the potential for AI-driven solutions in customer support, knowledge management, and interactive content creation.

Explore my [GitHub repository.](https://github.com/shubhammurti/AWS-Projects-Portfolio/)

> **Shubham Murti — Aspiring Cloud Security Engineer | Weekly Cloud Learning !!**

**Let’s connect:** [Linkdin](http://www.linkedin.com/in/shubham-murti-b6486a1aa), [Twitter](https://x.com/murti_shubham), [Github](https://github.com/shubhammurti)
