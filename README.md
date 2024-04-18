# Astute_Samsung_Prism

<img src = "https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/f3e5baab-ca64-4617-9d99-f801841636ab" width = "100%"/>

## Introduction

Welcome to the **Generative AI Workspace for Office Meetings!** This project empowers office workers to streamline their meeting experiences, fostering efficient communication and collaboration across language barriers.

### Key Features

- #### Meeting Management:
  Effortlessly manage your meetings by creating agendas, taking notes, and summarizing key points.
- #### Multilingual Understanding:
  Break down language barriers. The workspace leverages cutting-edge AI to understand meeting content in multiple languages.
- #### Question-Answering Engine:
  Gain deeper insights into your meetings or tasks. Ask the workspace questions about specific topics or action items, and receive tailored responses.

### Tech Stack
This Python-based solution leverages a powerful combination of libraries:

- #### LangChain:
  A comprehensive toolkit for building natural language processing applications.
- #### OpenAI API:
  Integration with OpenAI's advanced large language models unlocks functionalities such as text generation and summarization, significantly enhancing the platform's capabilities.
- #### Hugging Face Embeddings & FAISS Vectorstore:
  Enables efficient semantic search and information retrieval through large language models and vector similarity techniques.
- #### Whisper:
  A state-of-the-art speech-to-text library for accurate transcription of meeting audio in multi-languages.
- #### Google Translator:
  Provides seamless real-time translation capabilities for multilingual meetings.

## Architecture Diagram
![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/590f5e64-c5c0-48bf-96eb-c77eb7eb4428)

- ### Attend Meet:
  This initial step signifies the starting point, likely a video conferencing platform like Zoom or Google Meet, where the meeting is conducted.

- ### Recorded Video:
  The video recording of the meeting is captured from the conferencing platform.

- ### Transcript:
  The recorded video is converted into text using an automatic speech recognition (ASR) tool, such as Whisper.

- ### Generative AI Model:
  This block likely refers to a large language model (LLM) trained on a massive dataset of text and code.  The model can perform various tasks including text generation, translation, writing different kinds of creative content, and answering your questions in an informative way.

- ### MOM (Minutes of Meeting):
  The LLM presumably analyzes the meeting transcript and generates a summary of the discussion, capturing the key takeaways and decisions.

- ### Server:
  This denotes a storage server that likely houses the recorded video, transcript, and the generated MOM document.

- ### Content of E-mail:
  The system extracts key information from the MOM, likely including action items and decisions made, and prepares an email summarizing these points.

- ### E-mail Bot:
  An email automation tool is employed to deliver the email containing the meeting summary to the participants.
  
- ### Sending E-mail: The email bot delivers the email notification to the meeting participants.

- ### Questions, Agents, Tools:
  The system integrates with various productivity tools and services that can be used to follow up on meeting action items or to answer questions related to the meeting content..

- ### Answers:
  The system can potentially answer questions posed by users regarding the meeting content, leveraging the meeting transcript and MOM.

