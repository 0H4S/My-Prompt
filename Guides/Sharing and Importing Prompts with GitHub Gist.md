<div align="center">
  <h1>Prompt Import and Sharing Guide</h1>
  <p>Welcome to the prompt import system! You can now create, back up, and share your favorite prompts (or entire prompt packs) with the community through <b>GitHub Gist</b>. To ensure that <b>My Prompt</b> recognizes your prompts correctly, we have created a simple formatting system. Read the instructions below to master prompt creation.</p>
</div>

<hr>

<h2>File Name</h2>
<p>For the system to recognize the file and for the <b>"Import Prompt"</b> button to appear automatically on GitHub Gist, <b>it is strictly required</b> that the file name contains <code>.mp.prompt.</code> before the extension.</p>

|✅ Correct ✅|❌ Incorrect ❌|
|:------------:|:--------------:|
|`Translator.mp.prompt.txt`|`Translator.txt`|
|`Prompts.mp.prompt.json`|`Prompts.json`|
|`Data-Analysis.mp.prompt.md`|`Data-Analysis.md`|

<hr>

<h2>Settings</h2>
<p>In <code>.txt</code> and <code>.md</code> formats, each file represents <b>a single prompt</b>. If you want to set a clean title and enable advanced features, you can add a configuration line at the beginning of the file.</p>

<br>

<p><b>How it works:</b></p>
<ul>
  <li>It must be <b>exactly on the first line</b> of the file.</li>
  <li>It must be enclosed by two opening and two closing curly brackets: <code>{{ ... }}</code></li>
  <li>Parameters must be separated by a <b>semicolon</b> <code>;</code>.</li>
</ul>

<br>

<p><b>Available parameters:</b></p>
<ul>
  <li><code>title:</code> The name of your prompt.</li>
  <li><code>usePlaceholders:</code> <code>true</code> Enables Dynamic Prompt mode.</li>
  <li><code>autoExecute:</code> <code>true</code> Causes the prompt to be sent automatically upon clicking.</li>
</ul>

<br>

<p><b>Usage example on line 1:</b> <code>{{title: My Super Prompt; usePlaceholders: true; autoExecute: true}}</code></p>

<br>

<blockquote><p>💡 This first line is automatically cleared during import and will <b>not</b> appear in the body of your prompt. If you do not use this line, the system will use the file name as the title and leave the features disabled.</p></blockquote>

<hr>

<h2>Choosing the Ideal Format</h2>
<p>The system supports three formats, each with its own purpose.</p>

<br>

<h3>1. JSON — ⭐ Recommended</h3>
<p>The JSON format is the most powerful and secure. It is the <b>only format that allows you to import multiple prompts at once</b> (in bulk). Ideal for creating prompt packs (e.g., "SEO Pack", "Dev Pack").</p>

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

<br>

<h3>2. TXT — 🟢 Easy</h3>
<p>Ideal for those who just want to write the prompt quickly in a notepad and share it. The text is read exactly as it was written, preserving line breaks.</p>

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

<br>

<h3>3. MARKDOWN — 🟠 Less Recommended</h3>
<p>Although supported, pure Markdown format on GitHub Gist is rendered as HTML by the page. Our system features a built-in "reverse converter" that reads the visual output and transforms it back into Markdown text for your prompts. It can be used if you want to make the reading experience visually appealing on the Gist.</p>

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

<hr>

<h2>How to Share Your Prompts</h2>

<ol>
  <li><b>Account Requirements:</b> To <b>Share</b>, it is essential to have a GitHub Gist account. If you don't have one, register at <a href="https://gist.github.com">gist.github.com</a>. To <b>Import</b>, no authentication is required; public querying can be done directly via <a href="https://gist.github.com/search?o=desc&q=%22.mp.prompt.%22&s=updated">parameterized search</a>.</li>
  <li><b>File Identification:</b> In the <b>"Filename including extension..."</b> field, name the file adhering to the mandatory technical nomenclature: the <code>.mp.prompt.</code> suffix (e.g., <code>analysis-setup.mp.prompt.txt</code>).</li>
  <li><b>Data Insertion:</b> Enter the structured code of your prompt into the platform's main text editor.</li>
  <li><b>Visibility Configuration:</b> Set the privacy to <b>"Create public gist"</b>. This step is crucial for the prompt to be indexed and visible to other users.</li>
  <li><b>Finalization:</b> Once the Gist is published, the URL in your browser's address bar is the official link for sharing.</li>
</ol>

<p>When accessing a prompt's page on Gist, the interface will inject the <b>"Import Prompt"</b> button next to the <b>"Raw"</b> button. Triggering this command initiates the automatic integration with the system.</p>

<hr>

<div align="center">
  <h2>Examples</h2>
  <p>Check the <a href="https://gist.github.com/0H4S/07abfbdcca8c1b7cf71c40bcae15e77a">Examples</a> to see real prompts in action.</p>
</div>
