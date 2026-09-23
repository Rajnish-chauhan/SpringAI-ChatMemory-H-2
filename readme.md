# Spring Ai H-2 DB

![H-2DB](/images/img.png)


**In this project i'm learnt about --**
* ChatMemory
    * ChatMemory invisibly saves your past messages and automatically attaches them to your next prompt so the AI remembers the conversation context.
* JdbcChatMemoryRepository
    * It persists the AI and user messages into a relational database (like H2, PostgreSQL, or MySQL) using standard SQL. This ensures that if your application crashes or restarts, the user's chat history is not lost.
* MessageWindowChatMemory
    * Instead of loading an infinite, ever-growing chat history (which would eventually crash the AI with a "Context Window Exceeded" error and cost a lot of money), it only keeps the most recent 'N' messages. For example, it might only remember the last 10 interactions of the conversation and silently drop older ones.
* MessageChatMemoryAdvisor
    * It does the manual heavy lifting for you. When you send a new prompt, this advisor automatically fetches the history from the ChatMemory, invisibly attaches it to your prompt, sends it to the AI, and then automatically saves the AI's new reply back into the database. You never have to manually manage arrays of past messages