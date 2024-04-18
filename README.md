# Astute_Samsung_Prism

<img src = "https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/f3e5baab-ca64-4617-9d99-f801841636ab" width = "100%"/>

## Introduction

Welcome to the **Generative AI Workspace for Office Meetings!** This project empowers office workers to streamline their meeting experiences, fostering efficient communication and collaboration across language barriers.

### Note: The updated folder in repository also include the previous code which was submitted before deadline.

### Key Features

- #### Meeting Management:
  Effortlessly manage your meetings by creating agendas, taking notes, and summarizing key points.
- #### Multilingual Understanding:
  Break down language barriers. The workspace leverages cutting-edge AI to understand meeting content in multiple languages.
- #### Question-Answering Engine:
  Gain deeper insights into your meetings or tasks. Ask the workspace questions about specific topics or action items, and receive tailored responses.

### Tech Stack
This Python-based solution leverages a powerful combination of libraries:

- #### OpenAI Whisper:
  Used for transcribing audio files into text because it is a state-of-the-art speech recognition model that supports multiple languages.
- #### googletrans:
  Used for translation tasks because it provides a simple interface for translating text between multiple languages without requiring separate models for each language pair.
- #### LangChain:
  Utilized for question-answering and information retrieval tasks because it provides a convenient way to combine LLMs with vector stores and other components, enabling efficient and scalable question-answering pipelines.
- #### FAISS:
  Used as the vector store for storing and searching embeddings because it is an open-source library that provides efficient similarity search and retrieval capabilities.
- #### HuggingFaceEmbeddings:
  Used for generating embeddings because it is an open-source library that provides pre-trained models for generating embeddings, which are essential for similarity search and retrieval tasks.
- #### NLTK:
  Used for natural language processing tasks, such as tokenization and stop word removal, because it is a widely-used and well-maintained library for NLP tasks in Python.
- #### Similarity Search:
  Employed for retrieving relevant information from the transcript text because it allows efficient retrieval of the most relevant chunks of text based on the similarity of their embeddings to the input query.

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
  
- ### Sending E-mail:
  The email bot delivers the email notification to the meeting participants.

- ### Questions, Agents, Tools:
  The system integrates with various productivity tools and services that can be used to follow up on meeting action items or to answer questions related to the meeting content.

- ### Answers:
  The system can potentially answer questions posed by users regarding the meeting content, leveraging the meeting transcript and MOM.

## Code Implemetation
Let's delve deeper into the architecture, exploring its features in more detail.

### Multilingual Minutes of Meeting Creation:

This feature provides a solution for generating minutes of a meeting (MOM) in multiple languages. Here's a breakdown of the code and the approaches used:

- Language Selection:
  The code prompts the user to choose their preferred language for the MOM. This is achieved using the **language()** function, which maps the user's choice to a language code.
  
  ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/4b30c013-e213-410f-8d5e-05e7794d8356)

- File Conversion:
  The **mp4tomp3()** function allows converting an MP4 video file to an MP3 audio file using the ffmpeg command-line tool. This is a common step in audio processing pipelines.
  
  ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/aae99607-20ca-4276-805c-506a1350bf5f)

- Transcription:
  
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/9e315cc6-80a1-436b-845b-f59d34f405d3)
  
  - The **transcriptnormal()** function utilizes the OpenAI Whisper model to transcribe the audio file (MP3 format) into text.
  - The **translate_transcript()** function is used to translate the transcribed text into multiple languages. It leverages the googletrans library for translation.
  - This function detects the language of each segment in the text and translates it to the English Language.
  - The reason for using googletrans is its ability to handle multiple languages and provide translations without requiring a separate model for each language pair.

- TimeStamp Transcription:
  whisperx is an extension of the OpenAI Whisper model, which is a state-of-the-art speech recognition model capable of transcribing audio in multiple languages. The whisperx library provides additional features and enhancements on top of the base Whisper model.
  
  ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/b79d033e-3bb1-4f20-b8ca-4a8605f5d9cf)
  
  - Accurate Transcription: whisperx inherits the high accuracy of the Whisper model in transcribing speech from various languages, dialects, and accents.
  - Timestamp Information: One of the key benefits of using whisperx is its ability to provide timestamp information for each transcribed segment. In the provided code, the model.transcribe method returns a dictionary result containing a segments key, which holds a list of dictionaries representing each transcribed segment. Each segment dictionary includes the transcribed text, as well as the start and end timestamps for that segment.
  - CSV Output: The code demonstrates how to save the transcription results, including the timestamps, to a CSV file. This can be useful for various applications that require synchronization between text and audio/video content, such as generating subtitles, creating transcripts with timestamps, or performing analysis on specific portions of the audio.
  - Batch Processing: whisperx supports batch processing, allowing efficient transcription of longer audio files by splitting them into smaller chunks and processing them in parallel. In the provided code, the batch_size parameter controls the number of audio samples processed simultaneously, which can improve transcription performance, especially on GPU-accelerated systems.
  - Model Selection: whisperx offers different model variants, such as "large-v2" used in the provided code, which can be chosen based on the trade-off between accuracy and computational requirements.
  - Device Support: whisperx supports running on both CPU and GPU devices. In the provided code, the device="cuda" parameter specifies that the transcription should be performed on a CUDA-enabled GPU, which can significantly speed up the transcription process compared to running on a CPU.

- Minutes of Meeting Preparation:
  - The **translateentolang()** function is a helper function that translates English text to the desired target language using the googletrans library.
    
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/7dcf5325-d982-48c4-8f42-11bdfea55acf)
    
  - The **save_to_txt()** function writes the MOM components (title, agenda, summary, tasks, and important points) to a text file.
    
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/2a16e804-ed89-428e-8bd3-53cf1f64f4bf)
  
  - The **MOMAnswer()** function utilizes the LangChain library to perform question-answering on the transcript text.
    
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/1b561a08-ae08-4eb1-bda6-5d8550e6bb80)
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/7491da10-d6a4-4020-a648-f1fd2c441fc0)

    - It uses the **CharacterTextSplitter** to split the transcript into smaller chunks.
    - The **HuggingFaceEmbeddings** is used to generate embeddings for the text chunks, as it is an open-source library for generating embeddings.
    - The **FAISS vector store** is used to store the embeddings, as it is an open-source library for efficient similarity search and retrieval.
    - The **load_qa_chain** function is used to connect the **OpenAI language model (LLM)** to the FAISS vector store.
    - The reason for using LangChain is its ability to combine LLMs with vector stores for efficient question-answering and information retrieval tasks.
  - The MOM() function is the main function that orchestrates the entire process of generating the MOM.
    
    ![image](https://github.com/Aditya3012Purwar/Astute_Samsung_Prism/assets/103439955/cc9f3354-eca1-4051-a25f-bb5a08280fa2)
    
    - It preprocesses the transcript text by removing noise and performing text normalization.
    - It utilizes the **NLTK library (nltk.sent_tokenize, nltk.word_tokenize, nltk.corpus.stopwords)** for tasks such as sentence tokenization, word tokenization, and stop word removal.
    - It computes the word frequencies and sentence scores to identify the most important sentences in the transcript.
    - It uses the **MOMAnswer()** function to generate the title, agenda, tasks, and important points by querying the LangChain question-answering pipeline.
    - If the preferred language is not English, it translates the MOM components to the target language using the **translateentolang()** function and the googletrans library.
    - The reason for using NLTK is its ability to perform natural language processing tasks, such as tokenization and stop word removal, which are essential for text preprocessing and summarization.

The code demonstrates the usage of various open-source libraries and approaches to handle tasks such as audio transcription, translation, text preprocessing, embeddings generation, vector storage, and question-answering. The combination of these libraries and techniques allows for the generation of minutes of meeting in multiple languages, leveraging the strengths of each component.



