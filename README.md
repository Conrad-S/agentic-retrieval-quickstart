# Agentic Retrieval Quickstart

```
 - Description:    Demonstrates the new Agentic Retrieval feature in Azure Cognitive Search that executes parallel queries.
 - Feature Status: Preview
 - Code Status:    This sample working as of Oct 2, 2025
 - Language:       Python (used a .venv environment)
 - Documentation:  https://learn.microsoft.com/en-us/azure/search/search-get-started-agentic-retrieval?tabs=foundry-perms%2Csearch-endpoint&pivots=programming-language-python
```

# Notes:
Python Version
- If you are using an ARM processor I suggest using Python 3.12 and not 3.13 so that the latest openai and aiohttp packages install.

Azure Roles
- The instructions say to add the 'Cognitive Services User' role to your ID and the managed identity of the Foundry instance. This is required.
!! You must also add the 'Cognitive Services OpenAI User' role to both your ID and the managed identity of the Foundry instance.

Query Phrasing
- The first query in the instructions does not return results. After analysis I determined that this is due to the phrasing of the query.
- We should ask 'what' or 'how versus why'. The modified query returns results. Example:
      
>  Original Query (no results)
>  - Why is the Phoenix nighttime street grid is so sharply visible from space, whereas large stretches of the interstate between midwestern cities remain comparatively dim?
    
>  Modified Query (results)
>  - What makes Phoenix's urban street grid so visible from space at night? How does Phoenix's nighttime appearance compare to other cities?

Performance
- The agent:
  - breaks a user question into multiple queries (the framework controls this),
  - executes the queries in parallel (possibly multiple times),
  - semantically ranks and combines the results,
  - returns the resulting text to an LLM, which generates the final response to the user.

For the first query in this notebook, these steps took 9.2 seconds to complete.

C. Scott - Oct 2, 2025
