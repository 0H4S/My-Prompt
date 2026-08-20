# User Guide: "Enhance Prompt" Feature

Welcome to the basic guide for the **Enhance Prompt** feature of **My Prompt**. Here you will learn how to configure the advanced options to get the most out of this tool.

---

## Configuring Multiple System Prompts

The System Prompt is the instruction that tells the Artificial Intelligence how it should act. Instead of using just one, **My Prompt** allows you to create a menu with multiple behavior options to choose from when using it.

**Where to configure:** `⚙️ Settings → Advanced → "Enhance Prompt" Settings`

### How to create your options menu
Delete the default content and write your options following exactly this structure: `Title(Description){{Prompt}}`

**Important rules:**
1. **Minimum of 2 options:** If you add only one, the menu will not activate.
2. **Separation:** Leave at least one blank line between each block.
3. **Double curly braces:** The actual command for the AI must be inside double curly braces `{{Prompt Here}}`.

> **💡 Tip:** If you want to go back to using just a single fixed prompt, without a selection menu, simply delete everything and type your prompt normally, without the need to use titles, parentheses, or double curly braces.

---

## Configuring API Keys and Rotation

For the tool to work, you need to connect it to AI providers using API Keys. **My Prompt** supports several official providers.

| Provider | Where to get your Key |
| :---: | :---: |
| **Google Gemini** | [aistudio.google.com/api-keys](https://aistudio.google.com/api-keys) |
| **Groq** | [console.groq.com/keys](https://console.groq.com/keys) |
| **OpenRouter** | [openrouter.ai/settings/keys](https://openrouter.ai/settings/keys) |
| **Hugging Face** | [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens/new?tokenType=read) |
| **NVIDIA NIM** | [build.nvidia.com/settings/api-keys](https://build.nvidia.com/settings/api-keys) |

### Automatic Key Rotation
If you use the tool heavily, the provider might temporarily block your requests due to request limits. To bypass this, you can enter **multiple keys** from the same provider. The system will automatically alternate between them.

**How to do it:**
In the text box of the chosen provider, paste your keys separated by a **comma** or a **space**.
Example: `key1, key2, key3` or `key1 key2 key3`

---

## Using a Custom Provider

You can also connect external providers that are not in the list above using the **Custom** option. 

**Attention:** The chosen API must strictly follow the **OpenAI standard** to work.

When choosing this option, you will need to fill in 3 pieces of information provided by the platform you chose:
1. **API Key:** Your access credential.
2. **Base URL:** The API address. Important: It must strictly end with `/v1/chat/completions`.
3. **Model Name:** The exact code of the model. Example: `llama-3-70b`.

---

## Master "My Prompt" and Support the Project

This guide covers only the basics to get you started. Since **My Prompt** is a 100% free tool, its development takes a lot of time and effort. 

If you want to extract **the full power of the tool** and also help keep the project alive, consider purchasing my **Interactive Prompt Tutorial**. 

In the paid tutorial, you will have access to:
- ✅ **2 Ready-to-Use Professional System Prompts:** Just copy and paste them into your system to get incredible results.
- ✅ **In-Depth Configuration Guide:** Detailed explanations on how to structure the best instructions.
- ✅ **Mastery of Custom Mode:** An in-depth step-by-step guide on how to find and configure external APIs using the OpenAI standard.

**Purchase the tutorial, master the tool, and support my work here:** 👉 **[Purchase Prompt Tutorial on Ko-fi](https://ko-fi.com/s/edf0540604)**

> **⚠️ Security Note:** Never share your API keys publicly. Treat them like personal passwords.
