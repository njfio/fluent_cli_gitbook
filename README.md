# Welcome to FluentCLI

<figure><img src=".gitbook/assets/fluent_logo_small.png" alt=""><figcaption></figcaption></figure>



## Introduction

**FluentCLI** is a powerful command-line interface designed to streamline interactions with various AI workflow engines. As a versatile tool, it enables developers, IT professionals, and tech enthusiasts to automate and enhance their workflows efficiently. Currently, FluentCLI supports integration with FlowiseAI and LangFlow, with plans to extend support to other major AI engines that offer similar API interactions.

### Key Features

* **Multi-Engine Support**: FluentCLI currently supports FlowiseAI and is in the process of integrating LangFlow, making it easier to switch between different AI workflow engine services without vendor lock-in.
* **Dynamic Configuration**: Configure and manage interactions dynamically using JSON-based configurations for each integrated service.
* **Extensible**: Open to adding support for new AI engines, allowing FluentCLI to grow with your needs and the evolving tech landscape.
* **User-Centric Design**: Built with the end-user in mind, FluentCLI offers a straightforward command-line experience that simplifies complex tasks.
* **Robust Documentation**: Detailed documentation helps you get started quickly and make the most out of FluentCLI’s capabilities.

### Getting Started

To begin using FluentCLI, you'll need to set up the necessary configurations for the AI engines you intend to use. Follow the installation guide below to set up FluentCLI on your system.

### Installation **Prerequisite: Ensure Rust is installed on your system.**&#x20;

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## Installation Choice 1: Directly from the repository

1. Run `cargo install`

{% code overflow="wrap" %}
```bash
cargo install --git https://github.com/njfio/fluent_cli.git
```
{% endcode %}

2. This will install the `fluent` executable to

{% code overflow="wrap" %}
```
~/.cargo/fluent
```
{% endcode %}

3. Create a fluent profile directory.

> Creating this directory as a git repository allows your config.json and amber.yaml file to be versioned, protected, and used across any system you want to use `fluent` on.

```
mkdir ~/.fluent_cli
```

4. Download the config.json file from the repository.

[https://github.com/njfio/fluent\_cli/blob/main/fluent\_cli/config.json](https://github.com/njfio/fluent\_cli/blob/main/fluent\_cli/config.json)

5. Copy that file to your fluent\_cli profile path.

```
cp ~/Downloads/config.json ~/.fluent_cli
```

6. If you have not used amber, [https://github.com/fpco/amber](https://github.com/fpco/amber), you need to initialize the repository.

```
cd ~/.fluent_cli
amber init
```

> <mark style="color:orange;">MAKE SURE YOU SAVE THE RESULTING PRIVATE KEY IN A PASSWORD STORE</mark>

7. Create both the two necessary user `env` entries.

```bash
export AMBER_YAML=/path/to/your/user/profile/.fluent_cli/amber.yaml
export FLUENT_CLI_CONFIG_PATH=/path/to/your/user/profile/.fluent_cli/config.json
```

## Installation Choice 2: Clone the repository

These steps are very similar

1. **Clone the repository:**

```bash
git clone https://github.com/yourgithub/fluent_cli.git
```

2. **Navigate to the FluentCLI directory:**

```bash
cd fluent_cli
```

3. **Build the application:**

```bash
cargo build --release
```

4. Create the profile directory and copy the necessary files

```bash
mkdir ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/target/release/fluent ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/config.json ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/fluent_cli_autocomplete.sh ~/.fluent_cli
```

5. If you have not used amber, [https://github.com/fpco/amber](https://github.com/fpco/amber), you need to initialize the repository.

```
cd ~/.fluent_cli
amber init
```

> <mark style="color:orange;">MAKE SURE YOU SAVE THE RESULTING PRIVATE KEY IN A PASSWORD STORE</mark>

6. Create both the two necessary user `env` entries.

```bash
export AMBER_YAML=/path/to/your/user/profile/.fluent_cli/amber.yaml
export FLUENT_CLI_CONFIG_PATH=/path/to/your/user/profile/.fluent_cli/config.json
```

## Source the autocomplete script in your profile

```bash
source /Users/n/.fluent_cli/fluent_cli_autocomplete_v1.sh
```

## Add the necessary keys to your amber configuration

Fluent's transparent security feature looks for keys in the amber configuration named AMBER\_. During runtime, any entries in the flow's configuration will be replaced with the values from the amber vault.

{% code title=" amber encryption cmd" overflow="wrap" %}
```bash
amber encrypt AMBER_FLUENT_OPENAI_API_KEY_01 sk-tdfL2lwUJzFdTHVcwOitT3FlbkFJ7AEgQJCnGF4db3jvlvAO
```
{% endcode %}

Depending on the chatflows you want to run will depend on the API keys necessary to add to amber. The following is a table of keys that are configured with the config.json file.   You only need to include keys for the flows you want to run.

The following table lists all the current keys in the config.json file, a url where to get an API key from the service, and the command to run in your terminal.

## AMBER FLUENT ENV KEYS

<table data-card-size="large" data-view="cards" data-full-width="true"><thead><tr><th>Variable Name</th><th>API Key URL</th><th>Amber Command</th></tr></thead><tbody><tr><td><code>AMBER_FLUENT_SESSION_ID_01</code></td><td></td><td><code>amber encrypt AMBER_FLUENT_SESSION_ID_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_ANOTHERWEBSERVICE_NJF</code></td><td></td><td><code>amber encrypt AMBER_ANOTHERWEBSERVICE_NJF &#x3C;content></code></td></tr><tr><td><code>AMBER_LOCAL_FLUENT_DEFAULT_KEY</code></td><td></td><td><code>amber encrypt AMBER_LOCAL_FLUENT_DEFAULT_KEY &#x3C;content></code></td></tr><tr><td><code>AMBER_REPO_CLOUD_FLUENT_DEMO_KEY</code></td><td></td><td><code>amber encrypt AMBER_REPO_CLOUD_FLUENT_DEMO_KEY &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_ANTHROPIC_KEY_01</code></td><td><a href="https://console.anthropic.com/settings/keys">Anthropic</a></td><td><code>amber encrypt AMBER_FLUENT_ANTHROPIC_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_GROQ_API_KEY_01</code></td><td><a href="https://console.groq.com/keys">GroqLPU</a></td><td><code>amber encrypt AMBER_FLUENT_GROQ_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_MISTRAL_KEY_01</code></td><td><a href="https://console.mistral.ai/api-keys/">Mistral</a></td><td><code>amber encrypt AMBER_FLUENT_MISTRAL_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_OPENAI_API_KEY_01</code></td><td><a href="https://platform.openai.com/api-keys">OpenAI</a></td><td><code>amber encrypt AMBER_FLUENT_OPENAI_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_PERPLEXITY_API_KEY_01</code></td><td><a href="https://www.perplexity.ai/settings/api">Perplexity</a></td><td><code>amber encrypt AMBER_FLUENT_PERPLEXITY_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_GEMINI_API_KEY_01</code></td><td><a href="https://ai.google.dev/">Gemini</a></td><td><code>amber encrypt AMBER_FLUENT_GEMINI_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_COHERE_API_KEY_01</code></td><td><a href="https://dashboard.cohere.com/api-keys">Cohere</a></td><td><code>amber encrypt AMBER_FLUENT_COHERE_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_HUGGINGFACE_API_KEY_01</code></td><td><a href="https://huggingface.co/settings/tokens">HuggingFace</a></td><td><code>amber encrypt AMBER_FLUENT_HUGGINGFACE_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_REPLICATE_API_KEY_01</code></td><td><a href="https://replicate.com/account/api-tokens">Replicate</a></td><td><code>amber encrypt AMBER_FLUENT_REPLICATE_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_PINECONE_API_KEY_01</code></td><td><a href="https://app.pinecone.io/...">Pinecone</a></td><td><code>amber encrypt AMBER_FLUENT_PINECONE_API_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_SEARCHAPI_KEY_ID_01</code></td><td><a href="https://www.searchapi.io/">SearchAPI</a></td><td><code>amber encrypt AMBER_FLUENT_SEARCHAPI_KEY_ID_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_SERPAPI_KEY_01</code></td><td><a href="https://serpapi.com/manage-api-key">SerpAPI</a></td><td><code>amber encrypt AMBER_FLUENT_SERPAPI_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_ZEP_MEMORY_KEY_01</code></td><td><a href="https://app.getzep.com/projects/">ZepMemory</a></td><td><code>amber encrypt AMBER_FLUENT_ZEP_MEMORY_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_LEONARDO_AI_KINO_XL_MODEL_ID</code></td><td></td><td><code>amber encrypt AMBER_LEONARDO_AI_KINO_XL_MODEL_ID &#x3C;content></code></td></tr><tr><td><code>AMBER_MAKE_LEONARDO_IMAGE_POST</code></td><td></td><td><code>amber encrypt AMBER_MAKE_LEONARDO_IMAGE_POST &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_LANGSMITH_KEY_01</code></td><td><a href="https://smith.langchain.com/">LangSmith</a></td><td><code>amber encrypt AMBER_FLUENT_LANGSMITH_KEY_01 &#x3C;content></code></td></tr><tr><td><code>AMBER_FLUENT_GITHUB_PAT_KEY_01</code></td><td><a href="https://github.com/settings/tokens">Github PAT</a></td><td><code>amber encrypt AMBER_FLUENT_GITHUB_PAT_KEY_01 &#x3C;content></code></td></tr></tbody></table>

**Configure your AI engines:** Edit the `config.json` file to include your API keys and other necessary details for FlowiseAI and LangFlow.

#### Basic Usage

Here’s how you can send a basic request to an AI engine using FluentCLI:

```bash
fluent 
```

Replace `flowiseai` with `langflow` to switch between AI engines as needed.

### Support and Contribution

FluentCLI is an open-source project and welcomes contributions from the community. Whether it's adding new features, improving documentation, or reporting bugs, every contribution is appreciated.

### Roadmap

Looking ahead, FluentCLI aims to support additional AI workflow engines and introduce more user-friendly features based on community feedback. Stay tuned to our repository for the latest updates and feature releases.

