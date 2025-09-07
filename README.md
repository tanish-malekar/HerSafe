<div align="center">

# SafeSupportAI  

</div>

### Try it out
https://amazonbedrock.vercel.app/

### SafeSupportAI Features 💪

- **Discreet SOS Messaging through Steganography**  
  Women in abusive relationships are often unable to directly call out for help. Social media profiles and call histories are under constant surveillance by their abuser, making it difficult to seek assistance openly.  
   *Our Solution:* SafeSupportAI utilizes steganography to encode discreet distress messages within seemingly innocent images, allowing women to communicate in plain sight, without arousing suspicion.

- **AI Avatar for Mental Health Support**  
  Many survivors endure their struggles in silence, with only **10%** seeking mental health support.  
   *Our Solution:* A compassionate AI chatbot provides confidential support, offering personalized coping strategies and resources, especially important as women experiencing abuse are **80%** more likely to face mental health challenges.

- **Law Bot with Knowledge of Legal Rights**  
  In India, only **14% of women** have access to formal legal support. SafeSupportAI’s Law Bot helps change this by providing instant, confidential guidance on abuse cases, custody battles, and property claims.  
   *Our Solution:* Trained on the Indian constitution and other legal documents, the bot helps women gain the confidence to advocate for their rights, making legal support accessible to all.

---

## Detailed Description 📝

### 1. Discreet SOS Messaging through Steganography
For many women in abusive relationships who live under constant monitoring, finding a way to ask for help without alerting their abusers is critical. SafeSupportAI introduces a revolutionary SOS messaging system, using **steganography** to encode distress signals within innocent-looking images, like flowers or landscapes.

### How it Works 🛠️

On the user side, SafeSupportAI’s process begins with message generation, where the user enters brief details of their situation. Our LLM expands these inputs into complete, coherent sentences. The user then chooses an image prompt, like a flower or landscape, which the AI generates and encodes with the distress message through steganography. Once complete, the user shares this seemingly ordinary image on social media, where it appears innocuous to others, including any abusers monitoring the profile.

On the authority side, SafeSupportAI's system continuously monitors social media for SOS images tagged with specific hashtags. Once detected, these images are decoded to extract the hidden message using reverse steganography. The decoded text is then broken down into structured segments for efficient analysis, after which it is stored in MongoDB, where cases are organized by severity level to prioritize urgent responses.


![alt](https://i.ibb.co/LS6195k/napkin-selection-3.png)


![alt](https://i.ibb.co/X2GTbYc/napkin-selection-4.png)


### Technical Details 

| API Route            | Description                                                 |
|----------------------|-------------------------------------------------------------|
| `/text-generation`   | Expands user input via AWS Bedrock                        |
| `/img-generation`    | Generates an image from the user’s prompt                   |
| `/encode`            | Encodes text into the generated image                       |
| `/decode`            | Decodes text from the image                                 |
| `/text-decomposition`| Decomposes the decoded text into structured sections        |
| `/save-extracted-data` | Saves the structured data in MongoDB                       |

**Working**
**User Side**  
- Message Generation When the user inputs basic information about their situation, the LLM leverages this data to create syntactically complete, contextually relevant sentences that represent the user’s distress message.
- Image Creation The user selects a theme or prompt for an image (such as “flower,” “landscape,” or “food”), which the image generation module uses to create an innocuous-looking image with the selected theme.
- Message Encoding: The generated distress message is embedded into the AI-generated image using steganography, where the textual message is concealed within pixel data in a way that is imperceptible to the naked eye. This process uses encoding algorithms that maintain the image’s visual integrity while securely embedding the message.
- Sharing: The encoded image, which appears visually harmless, can be shared publicly on social media platforms. This avoids detection from an abuser monitoring the user's activity while providing a hidden channel for SOS messages.

**Authority Side**  
- Monitoring with Cron: A cron job runs at regular intervals to monitor social media channels for specific hashtags or identifiers associated with encoded SOS images. This background job allows the system to scan and detect potential distress signals in real time.
- Image Decoding: Once an image with an encoded SOS message is detected, it undergoes reverse steganography decoding. This involves extracting the pixel-embedded message, isolating the encoded data, and reconstructing it into a readable text format.
- Text Decomposition: The decoded message is analyzed and broken down into structured data fields (e.g., urgency level, nature of the abuse) using natural language processing techniques. This decomposition facilitates the classification of the message’s severity and content type.
- Storage in MongoDB: The parsed data is stored in MongoDB in a structured format, utilizing MongoDB’s document-based architecture to facilitate efficient retrieval and querying. Data fields are indexed for real-time access, enabling authorities to prioritize cases based on urgency and ensuring streamlined incident response.



##  **2. AI Avatar for Mental Health Support** 

For many survivors of abuse, the **psychological toll** is just as devastating as the physical harm. However, only **10%** of women experiencing domestic abuse seek mental health support, often due to fear of judgment, lack of privacy, or limited access to professional services.  
- Over **80%** of women facing abuse are at a higher risk of mental health issues such as **anxiety, depression**, and **PTSD**.  
- **SafeSupportAI** aims to bridge this gap, offering an accessible, **empathetic, and private** support system for women in distress.



###  **How It Works:**

**SafeSupportAI’s AI Avatar** provides **24/7 mental health support** through **confidential, non-judgmental conversations**. The avatar listens to users' concerns and offers:
- **Personalized coping strategies**  
- **Calming techniques**  
- **Relevant resources** to manage mental health, tailored specifically to the emotional needs of abuse survivors.

Whether a user experiences **panic attacks**, **emotional exhaustion**, or simply needs a safe space to express their feelings, **SafeSupportAI** is always there, offering a compassionate presence when needed most. The best part? It's completely confidential—no need to worry about being overheard or judged.
![Therapy bot](https://i.ibb.co/RhhLdm9/napkin-selection-1.png)



### 🛠️ **Technical Details:**

- **Model and Animation Loading:**  
  Upon initiating the conversation, the AI fetches **3D model files** (.glb format) and **animations** to bring the avatar to life. The avatar’s **facial morph targets** and animation sequences are initialized using **useGLTF**, allowing for **human-like interactions** with empathy.

- **User Data Retrieval:**  
  When a user interacts with the AI avatar, the system retrieves relevant data from previous conversations (stored **securely in MongoDB**) to offer a **personalized experience**. This enables the AI to understand the user’s emotional state, preferences, and history, ensuring continuity in support.

- **Natural Language Understanding:**  
  The AI uses a **Large Language Model (LLM)**, such as **Gemini**, to process the user’s input, understanding the **context**, **emotional tone**, and **urgency**. It then generates responses with **personalized coping strategies**, **calming techniques**, and other **mental health resources**.

- **Audio Generation and Lip-Sync:**  
  The AI’s responses are converted into **natural-sounding speech** using **ElevenLabs**’ **Text-to-Speech (TTS)** technology. The audio is base64-encoded, and synchronized with the avatar’s **lip movements**, ensuring **realistic lip-syncing**.

- **Facial Expression Mapping:**  
  **Titan Text G1 - Express** provides specific cues (e.g., **smiling**, **frowning**) that are mapped to the avatar’s morph targets. This allows the avatar to show appropriate **emotional expressions**, reflecting the user’s emotions such as **fear**, **sadness**, or **relief**.

- **Animation Management:**  
  The avatar transitions smoothly between different **animations** (e.g., from **Idle** to **Talking**), making the interaction feel natural and **engaging**, reinforcing the emotional tone of the conversation.


---

## **3. Law Bot for Legal Empowerment**

SafeSupportAI is not just about providing immediate emotional and physical safety—it’s about **empowering women** with the knowledge of their legal rights . Our **law bot**, equipped with an in-depth understanding of the Indian Constitution (and expanding to global legal frameworks ), provides **instant guidance** on abuse cases, custody disputes, and property claims, enabling women to navigate the complex legal landscape with confidence .

In many parts of the world, only 14% of women have access to formal legal assistance , often due to cultural barriers, financial constraints, or lack of awareness. SafeSupportAI aims to bridge this critical gap by offering **free, accessible legal guidance** at their fingertips 

### **How It Works: 🤖**

SafeSupportAI’s law bot is designed to provide **clear, understandable** information on a wide range of legal issues, tailored to the user’s unique situation . Women in need can simply ask the bot questions related to **abuse**, **divorce**, **child custody**, **property rights**, or other legal concerns, and receive instant, easy-to-understand responses based on national and international laws 

![Law Bot Image](https://i.ibb.co/cXR59by/napkin-selection-2.png)


### **Technical Details 🛠️**

**Preprocessing Phase (Document Embedding Preparation) :**
1. Collect legal documents, such as the Indian Constitution and related statutes 
2. Convert these documents into chunks if they are lengthy, ensuring each chunk captures meaningful information.
3. Pass each chunk through a vector embedding model (e.g., Sentence Transformers or Gemini/Vertex AI) to generate **dense vector representations**.
4. Store each vector embedding along with its associated text chunk in **MongoDB**, utilizing the vector storage capabilities (e.g., **MongoDB Atlas Vector Search**) for efficient retrieval.

**User Interaction Phase (Real-Time) :**
1. Receive the user’s question or legal query input 
2. Convert the user query into a **vector embedding** using the same embedding model to ensure compatibility with the stored embeddings.

**Vector Search and Retrieval :**
1. Conduct a vector similarity search in **MongoDB**, using the user query embedding to retrieve the most relevant document chunks.
2. Retrieve the top N most similar document chunks based on cosine similarity or another distance metric, ranked by relevance.

**Response Generation :**
1. Aggregate the retrieved document chunks and pass them to an **LLM** (e.g., Titan Text G1 - Express or a fine-tuned model) via the /text-generation API.
2. The LLM synthesizes a coherent and **legally sound** response based on the retrieved information.

**Bot Response :**
1. Present the generated response to the user in a **conversational format**.
2. Optionally, provide additional options for the user to ask follow-up questions or receive more detailed legal explanations.


---

### **How We Built It 🔧**

#### **Backend :**
- **Python 3.12 + FastAPI API development** 
- **Amazon Bedrock**: For text and embedding generation 
- **Amazon S3**: For Storage
- **Pymongo**: MongoDB connection 
- **Groq**: Fast AI Inference engine  that uses Gemma model
- **Pydantic**: Data modeling and validation 
- **Pypdf**: For formatting pdf documents
- **Black**: Linter and code formatter together with pr
- **Pillow**: For image manipulation during pre-commit hooks
- **MongoDB Atlas search**: For searching across vector embedding


#### **Frontend :**
- **Next.js** as the frontend framework 
- **Tailwind CSS** for styling 
- **Elevenlabs** for natual sounding text to speech generation
- **GLTF** (graphics library transmission format) for rendering 3D images on web
- **Amazon Bedrock** and **boto3**: For LLM inference
- **Clerk**: For authentication
- **Typescript**: Create functional components

#### **Deployment**
- **Render** for backend deployment 
- **Vercel** for frontend deployment 

