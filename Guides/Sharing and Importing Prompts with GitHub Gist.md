# Prompt Import and Sharing Guide

Welcome to the prompt import system! You can now create, back up, and share your favorite prompts (or entire prompt packs) with the community through **GitHub Gist**. To ensure that **My Prompt** recognizes your prompts correctly, we have created a simple formatting system. Read the instructions below to master prompt creation.

---

## File Name

For the system to recognize the file and for the **"Import Prompt"** button to appear automatically on GitHub Gist, **it is strictly required** that the file name contains `.mp.prompt.` before the extension.

| ✅ Correct ✅ | ❌ Incorrect ❌ |
| --- | --- |
| `Translator.mp.prompt.txt` | `Translator.txt` |
| `Prompts.mp.prompt.json` | `Prompts.json` |
| `Data-Analysis.mp.prompt.md` | `Data-Analysis.md` |

---

## Settings

In `.txt` and `.md` formats, each file represents **a single prompt**. If you want to set a clean title and enable advanced features, you can add a configuration line at the beginning of the file.

**How it works:**

* It must be **exactly on the first line** of the file.
* It must be enclosed by two opening and two closing curly brackets: `{{ ... }}`
* Parameters must be separated by a **semicolon** `;`.

**Available parameters:**

* `title:` The name of your prompt.
* `usePlaceholders:` `true` Enables Dynamic Prompt mode.
* `autoExecute:` `true` Causes the prompt to be sent automatically upon clicking.

**Usage example on line 1:** `{{title: My Super Prompt; usePlaceholders: true; autoExecute: true}}`

> 💡 This first line is automatically cleared during import and will **not** appear in the body of your prompt. If you do not use this line, the system will use the file name as the title and leave the features disabled.

---

## Choosing the Ideal Format

The system supports three formats, each with its own purpose.

### 1. JSON — ⭐ Recommended

The JSON format is the most powerful and secure. It is the **only format that allows you to import multiple prompts at once** (in bulk). Ideal for creating prompt packs (e.g., "SEO Pack", "Dev Pack").

```json
[
  {
    "title": "Efficient Summary",
    "text": "Lorem ipsum dolor sit amet\n\nConsectetur Adipiscing Elit\n\nLorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.\n\nMain Points:\n- Duis aute irure dolor in reprehenderit in voluptate.\n- Velit esse cillum dolore eu fugiat nulla pariatur.\n- Excepteur sint occaecat cupidatat non proident.\n\n1. Primus gradus\n2. Secundus gradus\n3. Tertius gradus\n\nSunt in culpa qui officia deserunt mollit anim id est laborum.",
    "usePlaceholders": true,
    "autoExecute": true
  }
]
```

### 2. TXT — 🟢 Easy

Ideal for those who just want to write the prompt quickly in a notepad and share it. The text is read exactly as it was written, preserving line breaks.

```text
{{title: Simple and Direct TXT; usePlaceholders: true; autoExecute: true}}
Lorem ipsum dolor sit amet

Consectetur Adipiscing Elit

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Main Points:
- Duis aute irure dolor in reprehenderit in voluptate.
- Velit esse cillum dolore eu fugiat nulla pariatur.
- Excepteur sint occaecat cupidatat non proident.

1. Primus gradus
2. Secundus gradus
3. Tertius gradus

Sunt in culpa qui officia deserunt mollit anim id est laborum.
```

### 3. MARKDOWN — 🟠 Less Recommended

Although supported, pure Markdown format on GitHub Gist is rendered as HTML by the page. Our system features a built-in "reverse converter" that reads the visual output and transforms it back into Markdown text for your prompts. It can be used if you want to make the reading experience visually appealing on the Gist.

```md
{{title: MD Formatted Prompt; usePlaceholders: true; autoExecute: true}}
# Lorem Ipsum Dolor Sit Amet

## Consectetur Adipiscing Elit

Lorem ipsum dolor sit amet, **consectetur adipiscing elit**. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

### Main Points:

* **Duis aute irure** dolor in reprehenderit in voluptate.
* **Velit esse cillum** dolore eu fugiat nulla pariatur.
* **Excepteur sint occaecat** cupidatat non proident.

1. Primus gradus
2. Secundus gradus
3. Tertius gradus

> "Sunt in culpa qui officia deserunt mollit anim id est laborum."
```

---

## How to Share Your Prompts

1. **Account Requirements:** To **Share**, it is essential to have a GitHub Gist account. If you don't have one, register at [gist.github.com](https://gist.github.com). To **Import**, no authentication is required; public querying can be done directly via [parameterized search](https://gist.github.com/search?o=desc&q=%22.mp.prompt.%22&s=updated).
2. **File Identification:** In the **"Filename including extension..."** field, name the file adhering to the mandatory technical nomenclature: the `.mp.prompt.` suffix (e.g., `analysis-setup.mp.prompt.txt`).
3. **Data Insertion:** Enter the structured code of your prompt into the platform's main text editor.
4. **Visibility Configuration:** Set the privacy to **"Create public gist"**. This step is crucial for the prompt to be indexed and visible to other users.
5. **Finalization:** Once the Gist is published, the URL in your browser's address bar is the official link for sharing.

When accessing a prompt's page on Gist, the interface will inject the **"Import Prompt"** button next to the **"Raw"** button. Triggering this command initiates the automatic integration with the system.

---

## Examples

Check the [Examples](https://gist.github.com/0H4S/07abfbdcca8c1b7cf71c40bcae15e77a) to see real prompts in action.
