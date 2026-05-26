# Synchronized External Prompt System

This document serves as a technical reference and implementation guide for the External Prompts architecture. The feature was developed to enable remote synchronization, version control, and mass distribution of text-based instructions.

This method is ideal for enterprise environments, teamwork, and industrial-scale usage, ensuring that all members of an organization utilize the latest, validated, and standardized versions of a prompt, without the need for individual manual updates.

---

## 1. System Architecture

The system operates on a client-request model, where the local machine periodically queries a central configuration file to verify the existence of new versions.

The structure requires three main components:
1. **Metadata File with .json extension:** The core of the system. It informs the client of the current version and where to find the corresponding text files.
2. **Prompt File with .txt or .md extension:** The raw content and instruction engineering.
3. **Changelog File with .txt or .md extension:** The documentation dashboard and change log.

---

## 2. Security Restrictions and Allowed Platforms

To prevent malicious code injection or data consumption by untrusted sources, the system enforces a strict restriction via a Whitelist.

The files involved, such as Metadata, Prompts, Changelogs, and Images, will only be accepted if they are hosted on the following domains:

| Platform | Domain |
|:----------:|:-------:|
| [GitHub](https://github.com) |`raw.githubusercontent.com` |
| [GitHub Gist](https://gist.github.com) |`gist.githubusercontent.com` |
| [GitLab](https://gitlab.com) |`gitlab.com` |
| [JSDelivr](https://www.jsdelivr.com) |`cdn.jsdelivr.net` |

> Users are strictly advised never to import metadata URLs from unknown sources, repositories, or authors.

---

## 3. Configuring the Repository

To implement this ecosystem in your organization, follow these structuring steps:

1. Create a public or internal repository on GitHub or GitLab. For Gist repositories, create a Gist containing the multiple files.
2. Organize the repository logically. It is recommended to create an isolated directory for each prompt.
3. Inside the folder, create the three required files. Example:
   * `meta.json`
   * `prompt.txt`
   * `changelog.md`

---

## 4. The JSON Metadata File

The JSON file is the conductor of the architecture. It must be constructed in compliance with the exact keys and character limits of the system.

### Format and Limits

| Keys | Requirement | Description |
|:------:|:---------:|:---------:|
| `title` | **Required** | Maximum of 50 characters. Longer titles will be truncated in the interface. |
| `version` | **Required** | Semantic versioning format, such as "1.0.0", "1.0.1", or "2.1.0". |
| `prompt` | **Required** | Valid, raw URL of the file containing the prompt. |
| `summary` | **Optional** | Summary of the prompt's function. Maximum of 200 characters. |
| `author` | **Optional** | Name of the author or team responsible for maintenance. |
| `changelog` | **Optional** | Valid URL of the history and documentation file. |
| `usePlaceholders` | **Optional** | Boolean value accepting true or false. Defines whether the file is a Dynamic Prompt using variable syntax compatible with **My Prompt**. The end user does not have permission to edit this configuration locally after importing. Therefore, it is strictly necessary for the administrator to declare the correct option in `meta.json`. |
| `autoExecute` | **Optional** | Boolean value accepting true or false. Defines whether the prompt should be submitted automatically after use. |

### Example of a Valid JSON Structure:

```json
{
  "title": "Example Prompt Title",
  "version": "1.0.0",
  "author": "Example Author or Team Name",
  "summary": "Example of a short descriptive summary explaining the purpose of this shared prompt.",
  "prompt": "https://raw.githubusercontent.com/example-user/example-repository/main/example-prompt.txt",
  "changelog": "https://raw.githubusercontent.com/example-user/example-repository/main/example-changelog.md",
  "usePlaceholders": true,
  "autoExecute": false
}
```

---

## 5. Essential URL Best Practices

For the ecosystem to function flawlessly and without residual cache blocking updates, web routing rules must be rigorously applied:

### A. Exclusive Use of RAW URLs
Any URL entered into the system, whether the initial JSON import link provided to users or the links declared within the JSON itself, **must point to the file in direct RAW format**.
* **Incorrect:** `https://github.com/user/repo/blob/main/prompt.md` because it renders the visual web page of the repository containing an HTML interface.
* **Correct:** `https://raw.githubusercontent.com/user/repo/main/prompt.md` because it delivers exclusively the pure text code.

### B. The Inverse Rule of URL Versioning
The handling of locations involves opposite dynamics depending on the purpose of the file:

**1. The JSON Metadata URL MUST be Static:**
When you share the system link for your team to perform the import, the .json file URL must never contain commit hashes or specific version tags in the address. The link must always point to the primary branch, such as main or master.
* **Reason:** If the user imports a JSON URL tied to a past version, such as commit a1b2c3d, the background verification system will continue reading that old file indefinitely. Consequently, future updates and the release of new versions will never reach the user interface.

**2. The Prompt and Changelog URLs MUST be Versioned:**
Inside your main static JSON file, the "prompt" and "changelog" keys should preferably point to URLs that contain the exact version tag or specific commit code, such as /v1.2.0/prompt.md.
* **Reason:** This ensures absolute integrity of the downloaded text, real version control, and acts as a natural cache bust on web servers. When your team releases a new version of the prompt, you only need to update the main JSON to point to the new versioned URL of the corresponding text files.

---

## 6. Rich Prompt Creation and the Evolution of the Changelog

The text foundation of the system is built from the two files described below.

### The Structuring of the Prompt File
Files intended for storing the instruction must strictly use the .txt or .md extensions.

Far more than housing a static paragraph of text, the prompt file allows for the advanced design of a **Dynamic Prompt**. The developer has full freedom to format and draft the document utilizing all the dynamic syntax compatible with the My Prompt system.

This means you can inject data input boxes, filling rules, selection lists, and variable calls directly into the body of the text. The system will interpret this syntax perfectly, converting the imported corporate file into an interactive tool the moment the operator uses it. Structure the text with technical precision to extract the best possible results from artificial intelligences.

### The Changelog File as a Documentation Portal
Although the name refers strictly to a log of version updates, the utility of this document goes far beyond simple change notes.

In this ecosystem, the Changelog operates as a complete documentation environment. The repository administrator can and should use this space to teach company users how to master the prompt. You can develop detailed descriptions about the logic behind the tool, present corporate use cases, display filling tips, and deepen workflows.

The system features a secure visual interpreter that will convert your text written in Markdown into interface components. The following visual formatting options are interpreted perfectly to assist in building your documentation:

| Description | Syntax |
|:----------:|:-------:|
|**Headings**|`# Heading 1` to `###### Heading 6`|
|**Dividing Lines**|`---`|
|**Lists**|Initiated with `- ` or `* `|
|**Bold Text**|`**text**`|
|**Italic Text**|`*text*`|
|**Links**|`[Link Text](https://url.com)`|
|**Inline Code**|\`code\`|
|**Code Blocks**|\`\`\`<br>code<br>\`\`\`|
|**Images**|`![Alternative Text](https://image-url.com)`|

**Strict Rule for Images in Documentation:**
The security barrier also acts on the loading of visual illustrations. Any and all images inserted into your instructional material via Markdown must be strictly hosted on one of the domains within the security Whitelist (GitHub, GitHub Gist, GitLab, and JSDelivr). If a graphic element points to a generic external domain, rendering will be preventively intercepted, displaying a red alert to protect the local operator.

Example of documentation in the Changelog file:

```markdown
# User Guide: BANT Qualifier v1.2.0

This tool has been optimized to align commercial requests with new company standards.

## How to use the new dynamic variables
In this version, we added a market niche selection menu. When running the tool, make sure to select the option corresponding to the investigated client to calibrate the weight of the questions.

## Update Notes
- Modified the context input variable to generate greater analytical rigor.
- Forced matrix formatting in the conclusion of the generated report.

## Visual Reference of the New Flow
![Corporate Mapping](https://raw.githubusercontent.com/YourCompany/prompts/main/assets/flow_v2.png)
```

---

## 7. User Experience and Local Limitations

It is crucial to guide all teams operating these tools regarding the mechanics inherent to the local client:

1. **Editing Lock and Read-Only Status:**
Synchronized External Prompts are locked in the user environment. Since these items derive from a central base, their nature blocks manual modifications. This factor eliminates process fragmentation and shields operations.

2. **Creation of Free Local Copies:**
Should a user find the need to adapt an official instruction to solve a specific challenge, they must create a local copy of the prompt. The system will generate an identical file, but completely severed from the cloud's umbilical cord, allowing unlimited formatting.

3. **Synchronization and Update Notices:**
The central engine performs seamless temporal scans respecting the window of days established by the user. If the numerical value registered in the version key in the remote JSON document is higher than the version stored on the machine, the user will receive an overlay alert. This screen will display a textual comparison between the owned version and the new one, requiring only affirmative consent to process and archive the new version perfectly.

---

## 8. Example Folder and Practical Test

To facilitate the implementation of the architecture described in this guide, I have prepared an example environment containing real and fully functional files. Analyzing a practical case hosted in a repository is the fastest and safest method to understand the communication dynamics between documents.

Visit the official demonstration folder in the project repository here: [Access Example Folder](https://github.com/0H4S/My-Prompt/tree/main/Guides/External%20Prompt)

Feel free to access the raw version of each of these three files, copy the source code in its entirety, paste it into your own corporate environment, and adapt the information according to your team's operational needs. Using these official templates as an initial baseline will ensure your first integration occurs quickly and without technical structuring errors.

### Perform a Practical Import Test

To visualize the system functioning in real time, you can run an import simulation directly in your local interface.

I have provided below the direct link pointing to the metadata file of this practical example. Simply copy the exact address listed below, paste it into the External Prompt URL field of your dashboard, and apply it.

**Copy and paste this link into your system:** `https://cdn.jsdelivr.net/gh/0H4S/My-Prompt@main/Guides/External%20Prompt/meta.json`
