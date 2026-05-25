# Prompt Usage Guide, Documentation, and Updates

This space goes far beyond a simple change log. It functions as an interactive documentation and a comprehensive usage manual for your shared prompt. Here, you can include detailed instructions, usage examples, and step-by-step guides so that your team knows exactly how to interact with the provided instructions.

---

## The Changelog as a Complete Usage Manual

Since this area supports rich Markdown, you can structure it to serve as a complementary guide containing:
- **Step-by-step instructions:** Explain how the user should initiate the conversation with the artificial intelligence.
- **Input and output examples:** Show practical examples of questions and the type of response expected from the AI.
- **Variables guide:** If your prompt uses dynamic placeholder filling, use this space to detail what should be entered in each field.

---

## Basic Formatting Features

You can organize usage instructions and highlight important parts of the text in a simple way:
- To make a word or phrase **bold**, place two asterisks at the beginning and the end of the section.
- To make a term *italic*, use just one asterisk at the beginning and the end.
- To create organized lists of steps or requirements, simply start the line with a hyphen followed by a space.
- To add external links, place the visible text between square brackets and the destination link between parentheses, for example: [Visit our Repository](https://github.com/0H4S/My-Prompt)

---

## Displaying Code and Command Examples

If your prompt requires technical instructions or if you want to show examples of commands that the user should copy, you can highlight them:

To highlight a short term or variable in the middle of a paragraph, wrap the text in a single backtick. E.g.: `example`.

For larger code blocks or structured data examples, use three backticks to open and close the block:

```json
{
  "example": "formatted field"
}
```

---

## How to Safely Insert Images and Flowcharts

You can display explanatory images, screenshots, or flowcharts in the guide to illustrate the expected behavior. The structure consists of an exclamation mark, the alternative text between square brackets, and the raw file URL between parentheses.

Example syntax:
![Explanatory Image Example](https://raw.githubusercontent.com/0H4S/My-Prompt/refs/heads/main/icon.svg)

Remember that the image must strictly be hosted on one of the authorized servers (GitHub Gist, GitHub, GitLab, and JSDelivr) so that the system can securely render it on the user panel.

---

## Best Practices for Keeping Your Documentation Updated
- Keep the usage instructions updated whenever there is a change in the main prompt rules.
- Describe the prompt's behavior in detail so that new team members can use it without prior training.
- Whenever you change this instruction manual or the changelog file, remember to update the version number in the main metadata file so that users receive the update notification and can view the new guide.
