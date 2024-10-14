# Introduction

Alexandria can work with word documents in two primray forms. 

* Chat with word document
* Creating books from word documents

This section will introduce you to these capabilities and their limitations.

# Chat with word document

Alexandria can allow you to attach a word document to a chat and have a discussion with it. 

To do this you should do the following steps

1. Login to alexandria
1. Click "ATTACH FILE" from the UI
1. Wait for the file to process (for larger files this may take 10+ seconds)
1. Ask a question such as "Can you summarize the attached file?"

Realistically you will ask different types of questions that might invoke different assistants. Examples include:

* "Can you review the attached contract for potential problems" which may invoke the legal contract assistant. 

Limitations include:

| Limitation | Summary |
|------------|---------|
| 250 MB File Size | to protect against denial of service attacks, we block uploading of documents greater than 250 MB in size |
| Images not supported | Images are currently ignored and considered when generating answers |
| 100 pages immediate questions | The AI is limited in what it an consume when you ask it a general question on a document. The specific length depends on the language of the document. But the rule of thumb is the first 100 pages of a document will be referenced in conversations |  

# Creating books from word documents

TBD