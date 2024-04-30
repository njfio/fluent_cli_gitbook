# The Config.Json File

A collapsed config.json file looks like this.

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 14.59.00.png" alt=""><figcaption><p>A folded config.json example</p></figcaption></figure>

A Flowise chatflow looks like this.

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.00.59.png" alt=""><figcaption><p>Example QA chatflow in Flowise</p></figcaption></figure>

This is a FluentCLI flow configuration for the above chatflow.

```
{
  "name": "FlowiseConversationalRetrivalQAChainRepoCloud",
  "engine": "flowise",
  "protocol": "https",
  "hostname": "9d81nz4o.rpcld.co",
  "port": 443,
  "chat_id": "225a8391-4e6b-4815-af6e-51993c2c2185",
  "request_path": "/api/v1/prediction/",
  "upsert_path": "/api/v1/vector/upsert/",
  "sessionId": "",
  "bearer_token": "AMBER_REPO_CLOUD_FLUENT_DEMO_KEY",
  "overrideConfig": {
    "chainName": "FlowiseConversationalRetrivalQAChainRepoCloud",
    "sessionId": "AMBER_FLUENT_SESSION_ID_01",
    "openAIApiKey": "AMBER_FLUENT_OPENAI_API_KEY_01",
    "searchApiKey": "AMBER_FLUENT_SEARCHAPI_KEY_ID_01",
    "accessToken": "AMBER_FLUENT_GITHUB_PAT_KEY_01",
    "pineconeApiKey": "AMBER_FLUENT_PINECONE_API_KEY_01",
    "repoLink": "https://github.com/FlowiseAI/Flowise/",
    "branch":  "main",
    "chunkOverlap": 500,
    "chunkSize": 3000,
    "recursive": true,
    "maxRetries" : 3,
    "language":{
      "codeTextSplitter_0": "js"
    },
    "modelName": {
      "chatOpenAI_0": "gpt-4-turbo-preview",
      "openAIEmbeddings_0": "text-embedding-3-large"
    },
    "returnSourceDocuments": true
  },
  "timeout_ms": 500000
},
```

This is also a FluentCLI flow configuration for the above chatflow.

```
{
  "name": "FluentCLIConversationalRetrivalQAChainRepoCloud",
  "engine": "flowise",
  "protocol": "https",
  "hostname": "9d81nz4o.rpcld.co",
  "port": 443,
  "chat_id": "225a8391-4e6b-4815-af6e-51993c2c2185",
  "request_path": "/api/v1/prediction/",
  "upsert_path": "/api/v1/vector/upsert/",
  "sessionId": "",
  "bearer_token": "AMBER_REPO_CLOUD_FLUENT_DEMO_KEY",
  "overrideConfig": {
    "chainName": "FluentCLIConversationalRetrivalQAChainRepoCloud",
    "sessionId": "AMBER_FLUENT_SESSION_ID_01",
    "openAIApiKey": "AMBER_FLUENT_OPENAI_API_KEY_01",
    "searchApiKey": "AMBER_FLUENT_SEARCHAPI_KEY_ID_01",
    "accessToken": "AMBER_FLUENT_GITHUB_PAT_KEY_01",
    "repoLink": "https://github.com/njfio/fluent_cli/",
    "branch":  "main",
    "chunkOverlap": 500,
    "chunkSize": 3000,
    "recursive": true,
    "maxRetries" : 3,
    "language":{
      "codeTextSplitter_0": "rust"
    },
    "pineconeIndex": "fluentcli",
    "modelName": {
      "chatOpenAI_0": "gpt-4-turbo-preview",
      "openAIEmbeddings_0": "text-embedding-3-large"
    },
    "returnSourceDocuments": true
  },
  "timeout_ms": 500000
},
```

## The difference in the above files.

Each of the above files will give Flowise AI enough details to execute the chatflow.    Each provides different runtime values though.   The first configuration is designed to upsert the FlowiseAI github repository and the second one is designed to upsert the FluentCLI github repository. &#x20;



## Required entries for all configuration files follow:

```
{
  "name": "FluentCLIConversationalRetrivalQAChainRepoCloud",
  "engine": "flowise",
  "protocol": "https",
  "hostname": "9d81nz4o.rpcld.co",
  "port": 443,
  "chat_id": "225a8391-4e6b-4815-af6e-51993c2c2185",
  "request_path": "/api/v1/prediction/",
  "sessionId": "",
  "bearer_token": "AMBER_REPO_CLOUD_FLUENT_DEMO_KEY",
  "overrideConfig": {
   }
   "tweaks": {
   }
  "timeout_ms": 500000
},
```

* name: The name that is called from the terminal after the fluent command.
* engine: The engine that the flow is configured to use.  \[flowise, langflow]
* protocol: https/http
* hostname: the hostname of your flowise or langflow server
* port: the port of service endpoint
* chat\_id: the unique flow id from flowise or langflow
* sessionId: a unique session id you can use across all chatflows.
* bearer\_token: points to an amber secret containing the api key
* overrideConfig: An array of override options available for almost all of the flowise chatflows
* tweaks: An array of override options availalbe for almost all of the langflow chatflows

## Creating a new Flowise Fluent configuration

First, open your config.json file in a code editor; something with JSON code folding is useful.  Then, duplicate one of the existing example flows.

1. Open one of your Flowise Chatflows,  and select the code icon in the upper right corner.

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.09.49.png" alt=""><figcaption></figcaption></figure>

2. In the resulting window, select `curl`

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.11.32.png" alt=""><figcaption></figcaption></figure>

3. You can grab the chat\_id in the curl window. It looks like 225a8391-4e6b-4815-af6e-51993c2c2185 above. Replace this entry in the chat\_id value of the flow.
4. Do the same for the hostname, `9d81nz4o.rpcld.co` above.
5. If you want to add any of the overrides, the options are all available in this window. They show how the JSON should be defined. In practice, this seems to work for a very large number of Flowise configurations.

I have noticed that some of the new Tool agents override through form, which will be addressed in the future. &#x20;

If you have done everything right up to this point, you should now be able to run. If anything is wrong, it should output a meaningful error about what part of the Environment or configuration is not working correctly.

```bash
fluent <your flow name> "This is my first fluent question'
```
