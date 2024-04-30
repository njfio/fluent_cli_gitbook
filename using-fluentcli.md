---
description: >-
  The core of fluent is taking the various types of input from a command prompt
  and allowing those to be combined in interesting ways to send to an AI LLM for
  processing.
---

# Using FluentCLI

***

### A most basic FluentCLI command example is:

This command calls the OpusChain (we don't know if it's Langflow or Flowise from here) and sends the request 'This is a test' to the chatflow.

A few moments later, the response is returned to the terminal as text.

```
fluent OpusChain 'This is a test'
```

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.42.39@2x.png" alt=""><figcaption></figcaption></figure>

***

### In this example, we echo the text, 'This is a test' to fluent's `stdin` input.  This is combined with the input question and sent to the OpusChain.   The two will be combined if I include a string in the request.

```
echo "This is a test" | fluent OpusChain ''
```

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.45.26@2x.png" alt=""><figcaption></figcaption></figure>

***

### In this request, we combine 'What is this?' with 'This is a test' and send it to the LLM.

```
echo 'this is a test' | fluent OpusChain 'What is this? '
```

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.46.24@2x.png" alt=""><figcaption></figcaption></figure>

> ### Any text can be piped into fluent through `stdin`.  However, token size limits do apply.  If you exceed the size limit, you will receive a response like this:

{% code overflow="wrap" %}
```json
{"statusCode":500,"success":false,"message":"Error: predictionsServices.buildChatflow - 400 {\"type\":\"error\",\"error\":{\"type\":\"invalid_request_error\",\"message\":\"prompt is too long: 202122 tokens > 199999 maximum\"}}","stack":{}}
```
{% endcode %}

***

### Adding file contents to the request payload

{% code overflow="wrap" %}
```bash
fluent OpusChain 'analyze these data points. ' --additional-context-file /Users/n/Downloads/Financial Sample.csv
```
{% endcode %}

<figure><img src=".gitbook/assets/CleanShot 2024-04-30 at 15.52.21@2x.png" alt=""><figcaption></figcaption></figure>
