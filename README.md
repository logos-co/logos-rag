The Logos Chatbot is constructed as a Retrieval Augmented Generation (RAG) Large Language Model (LLM). More specifically, the RAG workflow is modeled after a blog post from Anthropic on [Contextual Retrieval](https://www.anthropic.com/news/contextual-retrieval).  This is to aid in ensuring that the resultant LLM is more proficient at providing up-to-date and accurate answers when asked about anything that's happening with the [Institute of Free Technology](https://free.technology)(IFT). It is automatically fed updated information about the projects and their progress. For more specific information, please view the [sources](sources.md) document that tracks what is consumed and its current state. 

### Site
https://ask.free.technology

You will need to sign in with your Org Keycloak auth.

### Why was this created?
Easy! AI is all the rage. 

Just kidding (kinda). There is a tremendous amount of work being done across the IFT. As a result, it has become incredibly difficult to not only  keep track of what projects there are, but also the current state of any given project. This trends towards a lack of understanding throughout the organization, and a few people (the creator of this bot for instance) becoming key information hubs. 

This isn't sustainable, so we have created a bot that serves as a great source of information. This then serves as the entry-point for anything you'd like to know, and when it doesn't satisfy your curiosity, then it points you to the right source to learn more and hopefully contribute!

## Architecture
The chatbot is constructed as an [n8n](https://n8n.io) workflow connected to a self-hosted instance of [open-webui](https://github.com/open-webui/open-webui). In fact all the automations of the project are also n8n workflows and can be found in the [workflows](./workflows) directory (Not there yet, waiting for port to IFT infrastructure). 

For now, we use Claude 3.5 (both Sonnet and Haiku) API endpoints for the LLM and use our automation workflows to add contextual vectors from various sources to keep the knowledgebase up to date. There will be an additional effort to leverage all open-source and privately hosted models in the future such that this project is self-contained and hosted by the IFT. 
