# Essential Dynamic Prompt Guide
This document serves as a manual for structuring interactive forms, capturing variables, creating selection menus, and automating data insertion into your prompt before it is sent to the Artificial Intelligence.

---

## Syntax Table
Below are all the commands available in the system. They can be combined to create prompts ranging from the simplest to the most complex.

| Feature | Syntax / Example | What it does |
| :--- | :--- | :--- |
| **Free Text Input** | `[Label]` | Creates a simple text box. The text between brackets serves as the title in the form. |
| **Input + Variable** | `[Label = $var]` | Creates the field, displays the response at the declaration location, and stores it in the variable `$var` for reuse. |
| **Clean Variable** | `{Label = $var}` | Uses curly braces `{}`. Captures the information but hides the declaration from the final text. The value only appears where `$var` is called. |
| **Variable Call** | `$var` | Injects previously entered or selected content into any part of the prompt. |
| **Default Value (Text)** | `[Label :: Default]` | Pre-fills a text field or variable with a default value. |
| **Default Selection (Menu)**| `[Option :: x]` | Leaves a menu option pre-selected by default to save the user clicks. |
| **Comments** | `[Label](Tip)` | Adds a visual instruction next to the element. Must be attached directly, with no space before the parentheses. |
| **Menu Block** | `#start` ... `#end` | Delimits a menu region. Requires exact symmetry (e.g., if you open with `###start`, close with `###end`). |
| **Group Title** | `# Group Title` | Creates a header within the menu to organize blocks of options (required for separating groups). |
| **Multiple Choice** | `+ [Option]` | Allows selecting multiple options simultaneously within the menu. |
| **Single Choice** | `- [Option]` | When this option is selected, others in the same group are automatically deselected. |
| **Choice by ID** | `1 [Option A]`<br>`1 [Option B]` | Creates an advanced exclusion rule. Options with the same ID number cannot be selected together. |
| **Inline Menu** | `#start // + [A] // #end`| Creates a menu on a single line. Using `//` is mandatory to separate the title and options. |
| **"Other" Option** | `[#]` | Creates a special option that, when checked, opens a free text field. Does not require a prefix. |
| **Hidden Value (Payload)**| `'Text for the AI'` | Keeps the interface clean. The user clicks the Option, but the AI receives the text between quotes. Accepts variables internally. |
| **Protection Block** | `#ignore` ... `#end` | Prevents the reading of dynamic commands in the region. Treats system codes and syntaxes as plain text. |
| **Character Escape** | `\[Text\]` or `\:\:` | The backslash `\` neutralizes a specific character (e.g., prevents brackets from becoming text boxes). |
| **Date and Time** | `#date` / `#time` | Injects the current date/time. Accepts combinations and suffixes such as `-SS`, `-YY`, `+date`, `+time`. |
| **File Upload** | `#file(Instruction)` | Creates a zone for attaching documents that will be read only in the current session, saving system memory. |

---

## How to Build Your Dynamic Prompt
Building a dynamic prompt is like constructing an interactive form merged with the AI's instruction text. You don't need to be a programmer—just follow the logic of blocks:

1. **Start with data collection (Inputs and Variables):**
   If you need global information (such as "Customer Name" or "Tone of Voice"), declare it at the top. Use Clean Variables `{Label = $var}` if you want the prompt to stay organized and invisible at the top, calling `$var` only where the AI actually needs to read the information.

2. **Create Selection Menus:**
   Use `#start` and `#end` to wrap the user's choices. Remember to give it a title (`# Choose the format:`) and use the correct prefixes (`+` for multiple choice, `-` for single choice). 
   *Pro Tip:* Use **Hidden Values** (`'text'`) right below or beside the options if you want the interface to remain minimalistic for the user while delivering dense, complex instructions to the AI.

3. **Integrate System Tools:**
   Need the user to send a spreadsheet or PDF as context? Add a `#file(Attach the document here)`. Need to precisely record the moment the report was generated? Place a `#date+time` in the footer.

4. **Protect text that isn't commands:**
   If your prompt contains code snippets or literal brackets `[ ]` that the AI needs to read (and that shouldn't turn into text boxes), escape them individually with `\[ \]` or place the entire snippet inside a block delimited by `#ignore` and `#end`.

---

## What NOT to Do and Precautions

- **Forgetting to close blocks or braces:** Never leave a bracket open `[Label` or start a `#start` / `#ignore` without its respective `#end`. The system needs exact delimiters to function.
- **Ignoring the symmetry rule:** If you open a menu with `###start`, closing with `#end` will cause an error. The number of special characters must be identical in the opening and closing. The same applies to hidden values with quotes (e.g., `'''text'''`).
- **Improper spacing:** When calling a variable, never put a space between the dollar sign and the name (Use `$name` and not `$ name`). The same applies to comments: do not put a space before the parentheses (Use `[Option](Tip)` and not `[Option] (Tip)`).
- **Unnecessary use of Uploads:** A single `#file` field already allows the user to upload multiple files. Do not clutter the prompt by creating multiple repeated `#file` fields.

---

## Practical Example for Import

To understand how all this theory works in a real-world scenario, we provide a prompt file containing an example of a Dynamic Prompt. You can import this file into your system to view the source code side-by-side with the generated form.

👉 **[Import Prompt](https://gist.github.com/0H4S/8c5523271136eafb9a5024d2cd4b402b#file-example-dynamic-prompt-mp-prompt-json)**

---

## Supplementary Study Material
Did you have difficulty understanding the symmetry logic, hidden values, grouped block formatting, or how to structure complex prompts with interconnected variables? 

We have prepared an **Interactive Dynamic Prompt Tutorial** designed to teach everything from basic theory to the most advanced professional techniques, with examples you can test in practice.

👉 **[Purchase the Complete Interactive Tutorial](https://ko-fi.com/s/5bae55a949)**
