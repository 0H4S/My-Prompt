# [DEPRECATED] How to Use and Configure the "Enhance with AI" Feature

This document presents the technical instructions for the advanced configuration of the **"Enhance with AI"** feature. The objective of this guide is to detail the structuring of multiple **System Prompts** for workflow optimization and the implementation of an API key rotation system to ensure high availability and mitigate blocks due to excessive requests.

---

## Configuring Multiple System Prompts

The "System Prompt" acts as the fundamental guideline that instructs the language model on how it should interpret and process user inputs.

Instead of limiting the system to a single static instruction, the platform allows for the creation of a dynamic selection menu. With this functionality, users can register different behavioral profiles for the artificial intelligence and, at the time of execution, choose which guideline is most suitable for the current task.

### Location Within the System

To begin configuring your prompts, navigate through the following path in the system menu: `⚙️ Settings → Advanced → "Enhance with AI" Settings`

Locate the text area designated for the default System Prompt. To implement the multiple-choice menu, it is necessary to erase the existing content and structure the new options by strictly following the syntax below.

### Construction Rules and Syntax

The system uses a text parsing method that requires specific formatting to identify what constitutes the option title, the description, and the command (prompt) itself.

The fundamental structure of each block must be: `Title(Description){{Prompt}}`

**Mandatory Parameters:**

1. **Minimum Quantity:** It is strictly necessary to configure two or more options. If only one block is inserted using this syntax, the system will ignore the formatting and will not activate the selection menu.
2. **Spacing:** There must be at least one blank line separating each instruction block.
3. **Delimiters (Braces):** The body of the prompt—in other words, the actual instruction that will be sent to the AI—must be contained within double braces `{{ ... }}`. The system will fail to recognize the option if the braces are omitted or used singly `{ ... }`.

**Accepted Structuring Formats:**

The system supports both single-line instructions and complex instructions with line breaks.

- **Single-line formatting example:**

```text
Technical Reviewer(Corrects spelling errors){{Your role is to review the provided text and correct grammatical errors.}}
```

- **Multi-line formatting example:**

```text
Corporate Translator(Formal translation to English){{
Your role is to act as a corporate translator.
Translate the provided text into English.
Maintain a strictly professional tone suitable for business communications.
}}
```

### Practical Implementation Example

Below, we present a ready-to-use configuration template. Copy the text block, paste it into the System Prompt field, and execute the **"Enhance with AI"** feature. A selector will be displayed for you to choose which processing method you wish to apply.

```text
Code Reviewer(Analyzes and optimizes code snippets){{
You act as a Senior Software Engineer. Upon receiving a code snippet, your role is to:
1. Identify possible syntax or logic errors.
2. Suggest performance optimizations.
3. Return the corrected code accompanied by brief technical comments.
}}

Summary Generator(Synthesizes long texts into bullet points){{
Act as a data analyst. Read the text provided by the user and extract the most important information.
Present the result in a bullet-point list format, ensuring that the central idea of the original text is preserved, yet in a concise manner.
}}
```

**Returning to Simple Mode:**
If you wish to deactivate the selection menu and revert to using a single fixed instruction, simply clear the text field and insert your prompt directly, without using titles, parentheses, or double braces.

---

## API Key Rotation System

To process requests in the **"Enhance with AI"** feature, it is necessary to establish a connection with external Artificial Intelligence providers through authentication keys (API Keys).

### Compatible Providers

Currently, **My Prompt** has certified integration with the platforms listed below. You must create an account with your chosen providers and generate the respective keys.

| Provider | Access Link to Obtain Key |
| :--- | :--- |
| **Google Gemini** | https://aistudio.google.com/api-keys |
| **LongCat** | https://longcat.chat/platform/api_keys |
| **Groq** | https://console.groq.com/keys |
| **OpenRouter** | https://openrouter.ai/settings/keys |
| **Hugging Face** | https://huggingface.co/settings/tokens/new?tokenType=read |

### How Automatic Rotation Works

Continuously sending requests through a single API key can result in temporary blocks (known as *Rate Limit* or *Too Many Requests* errors). To address this technical limitation, **My Prompt** features a **key rotation (cycling)** resource.

This mechanism allows you to register multiple keys belonging to the same provider. The system autonomously alternates the key used with each new request made. This distributes the processing load across different keys, increasing the overall stability of the tool and preventing interruptions in your workflow.

### Instructions for Configuring Keys

**To implement rotation:**
1. Navigate again to `⚙️ Settings → Advanced → "Enhance with AI" Settings`.
2. Identify the field corresponding to your chosen AI provider.
3. Enter your multiple keys in the same text box, separating them with a **comma** or **space**.

**Examples of correct input:**
- `key1, key2, key3`
- `key1 key2 key3`

### Maintenance and Security Guidelines
- **Key Auditing:** Maintain strict control over which keys are active. If one of the providers revokes access to a key or it becomes invalid, remove it immediately from the system settings to prevent the rotation mechanism from directing requests to an inoperative credential.
- **Access Management:** Use the multiple-key feature judiciously. Excessive creation of accounts through automation may lead platforms to adopt permanent blocking measures against the user.
- **Confidentiality:** API keys carry the same level of criticality as access passwords. Never expose these alphanumeric sequences in public repositories, forums, or unsecured sharing channels.
