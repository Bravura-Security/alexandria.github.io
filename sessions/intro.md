---
title: Sessions
nav_order: 5
---

# Sessions

Sessions are the core user interaction with alexandria. A session is:

* A chat thread people have with alexandria.
* Users have multiple questions and get multiple responses from the AI in a session.
* People can share a session with others via link sharing.

# Responses

A response is a a question/answer response. When users ask questions, the following steps are taken:

* Alexandria will review the users qustion and select the best assistant for answering the question.
* Alexandria will then pass the question to the selected assistant. 
* The selected assistant will then work the question. It will:
  
    * Leverage tools to retrieve information that might be required
    * Invoke subsequent tools based on the knowledge generated from past tool requests. 
    * Generate supporting evidence like download urls for some of the information being consumed by the AI. 

* The selected assistant will then ultimately generate its response to the users question. 

Elements that are unique to responses include:

* People can vote on the quality of the response the Assistant is given. 
* People can give a comment that allows them to explain what they like and dislike about the response. 