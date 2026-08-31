🕵️ CSS Forensics

«A client-side CSS intelligence & forensic analysis toolkit.»

CSS Forensics is a lightweight developer tool for analyzing CSS stylesheets and detecting common maintainability, consistency, and code-quality issues.

It scans your stylesheet directly in the browser and turns raw CSS into a structured forensic report — including selector statistics, declaration counts, repeated declarations, "!important" usage, color systems, suspicious "z-index" values, property frequency, and more.

No backend. No framework. No build step. Your CSS stays in your browser.

---

✦ Features

📊 Stylesheet Statistics

Get an instant overview of your stylesheet:

- Total selectors
- Total declarations
- "!important" usage
- Duplicate declarations
- Unique colors
- Property frequency
- Number of detected findings

---

🚨 Risk Detection

CSS Forensics searches for patterns that can make a stylesheet harder to maintain.

Currently detects:

- Excessive "!important"
- Repeated declarations
- Duplicate property/value combinations
- Extremely high "z-index" values
- Large color systems
- Repeated CSS values
- Potential maintainability issues

Findings are categorized by severity:

Severity| Meaning
🔴 "HIGH"| Potentially problematic pattern
🟡 "MEDIUM"| Something worth reviewing
🔵 "INFO"| Informational observation

---

🎨 Color System Analysis

CSS Forensics extracts colors from your stylesheet and calculates how frequently each one appears.

Example:

COLOR SYSTEM

#ffffff  ███████████████████  17
#111111  ███████████          10
#6c5ce7  ██████                6
#ff4757  ███                   3

Supported color formats include:

#fff
#ffffff
#ffffff80

rgb(...)
rgba(...)

hsl(...)
hsla(...)

red
blue
green
black
white
...

This can help identify unnecessarily fragmented color systems and repeated hard-coded values.

---

📈 Property Frequency

The analyzer also calculates which CSS properties appear most frequently.

Example:

PROPERTY FREQUENCY

color        █████████████████  18
padding      ███████████        12
margin       █████████           9
background   ███████             7
display      █████               5

This gives you a quick overview of the structure and habits inside a stylesheet.

---

🔍 Duplicate Detection

One of the main purposes of CSS Forensics is finding repeated declarations.

For example:

.card {
    padding: 20px;
    padding: 20px;
}

CSS Forensics reports:

HIGH
Duplicate padding: 20px

Same declaration appears repeatedly.

It can also detect repeated property/value combinations across different selectors.

---

⚠️ "!important" Detection

Using "!important" isn't automatically wrong, but excessive usage can indicate problems with specificity or the cascade.

Example:

.button {
    color: white !important;
}

.card {
    background: red !important;
}

The analyzer tracks these occurrences and reports them.

For larger usage:

HIGH

Heavy !important usage

8 priority overrides detected.

---

🧱 High "z-index" Detection

Extremely large stacking values are often a sign of a stylesheet that has accumulated arbitrary values over time.

For example:

.modal {
    z-index: 99999;
}

CSS Forensics flags values above the configured threshold.

Example:

MEDIUM

High z-index: 99999

Extremely high stacking value.

---

🖥️ Interface

The UI is designed around a forensic / developer-tool aesthetic.

┌─────────────────────────────────────────────────────────────┐
│ { }  CSS FORENSICS                         LOAD   ANALYZE   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  STYLESHEET                  FORENSIC RESULTS              │
│                                                             │
│  01 :root {                  SELECTORS     24              │
│  02   --primary: #6c5ce7     DECLARATIONS 81              │
│  03 }                         !IMPORTANT    7              │
│  04                           DUPLICATES    4              │
│                                                             │
│                              COLOR SYSTEM                  │
│                              #ffffff █████████             │
│                                                             │
│                              RISK SIGNALS                  │
│                              ! Heavy !important usage     │
│                                                             │
└─────────────────────────────────────────────────────────────┘

The interface is:

- Dark themed
- Responsive
- Keyboard-friendly
- Dependency-free
- Designed for developer workflows

---

🚀 Getting Started

CSS Forensics doesn't require Node.js, npm, a server, or any build system.

1. Clone the repository

git clone https://github.com/KILLERDUTCH/CSS-Forensics.git

2. Open the project

cd CSS-Forensics

3. Run it

Simply open:

index.html

in your browser.

That's it.

---

🧩 Usage

Step 1 — Paste CSS

Paste your stylesheet into the editor.

body {
    margin: 0;
    color: #fff;
    background: #111;
}

Step 2 — Analyze

Click:

ANALYZE CSS

or use:

CTRL + ENTER

Step 3 — Inspect the report

The dashboard will generate:

- Statistics
- Color analysis
- Risk signals
- Findings
- Property frequency

Step 4 — Export

Click:

EXPORT JSON

to generate:

css-forensics-report.json

---

🔐 Privacy

CSS Forensics is designed as a 100% client-side application.

Your stylesheet is processed locally by JavaScript inside your browser.

YOUR CSS
   │
   ▼
BROWSER
   │
   ├── Parser
   ├── Analyzer
   ├── Detector
   └── Report Generator
   │
   ▼
FORENSIC REPORT

There is currently:

- ❌ No backend
- ❌ No database
- ❌ No account
- ❌ No upload API
- ❌ No analytics service
- ❌ No external CSS framework

Your CSS does not need to leave your browser.

---

🧠 How It Works

The analysis pipeline is intentionally simple and transparent.

CSS Input
    │
    ▼
Comment Removal
    │
    ▼
Rule Extraction
    │
    ▼
Declaration Parsing
    │
    ├───────────────┐
    ▼               ▼
Property Stats    Color Detection
    │               │
    ▼               ▼
Duplicate Scan   Color Frequency
    │               │
    └───────┬───────┘
            ▼
       Risk Analysis
            │
            ▼
       Report Builder
            │
            ▼
      Interactive UI

The current parser uses browser-side JavaScript and regular-expression-based extraction.

This makes the project intentionally lightweight, but also means it is not intended to replace a full CSS parser or production-grade linter.

---

🛠️ Tech Stack

CSS Forensics is intentionally built without frameworks.

Core

- HTML5
- CSS3
- Vanilla JavaScript
- DOM APIs
- Blob API
- Local browser processing

No dependencies

0 npm packages
0 frameworks
0 build tools
0 backend services

This makes the project extremely easy to run, fork, modify, and understand.

---

📁 Project Structure

The entire application is currently contained inside a single file:

CSS-Forensics/
│
├── index.html
└── README.md

The HTML file contains:

index.html
│
├── HTML
├── <style>
│   └── Complete UI
│
└── <script>
    └── Analyzer

This structure is intentional for the current version.

It allows the project to be downloaded or cloned and opened immediately without installing anything.

---

🧪 Example

Input:

body {
    color: #ffffff;
    background: #111111;
    z-index: 9999;
}

.card {
    padding: 20px;
    padding: 20px;
    background: #111111 !important;
}

.button {
    color: #ffffff !important;
}

Possible report:

SELECTORS
3

DECLARATIONS
8

!IMPORTANT
2

DUPLICATES
1

Findings:

HIGH
Duplicate padding: 20px

MEDIUM
High z-index: 9999

MEDIUM
!important used on background

MEDIUM
!important used on color

---

📤 JSON Export

Analysis reports can be exported as JSON.

Example structure:

{
  "selectors": 3,
  "declarations": 8,
  "important": 2,
  "colors": {
    "#ffffff": 2,
    "#111111": 2
  },
  "properties": {
    "color": 2,
    "background": 2,
    "padding": 2,
    "z-index": 1
  },
  "findings": []
}

This makes it possible to use the analysis data in future automation tools.

---

⌨️ Keyboard Shortcuts

Shortcut| Action
"CTRL + ENTER"| Analyze CSS
"CMD + ENTER"| Analyze CSS on macOS

---

📱 Responsive Design

CSS Forensics works across:

- Desktop
- Laptop
- Tablet
- Mobile

On smaller screens, the editor and report automatically switch to a single-column layout.

---

🗺️ Roadmap

The current version is only the beginning.

v1.x

- [x] CSS statistics
- [x] Selector counting
- [x] Declaration counting
- [x] "!important" detection
- [x] Duplicate detection
- [x] Color extraction
- [x] Property frequency
- [x] High "z-index" detection
- [x] Risk signals
- [x] JSON export
- [x] Responsive UI

v2.x

- [ ] Specificity analyzer
- [ ] Unused selector detection
- [ ] Duplicate selector detection
- [ ] CSS variable recommendations
- [ ] Repeated value detection
- [ ] Shorthand property detection
- [ ] Deep nesting detection
- [ ] "@media" analysis
- [ ] "@keyframes" analysis
- [ ] "calc()" analysis
- [ ] "var()" dependency graph

v3.x

- [ ] Interactive specificity graph
- [ ] CSS cascade visualizer
- [ ] Selector dependency map
- [ ] Advanced parser
- [ ] Performance heuristics
- [ ] Large stylesheet optimization
- [ ] Before / after comparison
- [ ] Shareable reports
- [ ] CLI version
- [ ] GitHub Action

---

💡 Future Vision

The long-term goal isn't to make another CSS formatter.

CSS Forensics aims to become a small CSS intelligence platform.

Instead of simply asking:

«"Is this CSS valid?"»

the project focuses on questions such as:

«"Why is this stylesheet becoming difficult to maintain?"»

«"Where are the suspicious patterns?"»

«"What parts of this CSS deserve attention?"»

«"How consistent is this stylesheet?"»

That distinction is the core idea behind the project.

---

🤝 Contributing

Contributions are welcome.

If you have an idea for a new detector, UI improvement, parser enhancement, or performance optimization:

1. Fork the repository.
2. Create a feature branch.

git checkout -b feature/my-feature

3. Make your changes.
4. Test the project locally.
5. Commit your changes.

git commit -m "Add my feature"

6. Push the branch.

git push origin feature/my-feature

7. Open a Pull Request.

---

🐛 Issues

Found a bug?

Open an issue and include:

- Browser
- OS
- CSS that reproduces the issue
- Expected behavior
- Actual behavior
- Screenshot if applicable

The more reproducible the issue is, the easier it is to fix.

---

⚠️ Limitations

The current parser is intentionally lightweight.

It is not a replacement for:

- Stylelint
- PostCSS
- CSSTree
- Browser DevTools
- Full CSS parsers

Complex CSS constructs may not always be interpreted perfectly.

For example:

@supports (...) {
    ...
}

@media (...) {
    ...
}

@layer components {
    ...
}

Advanced parsing is planned for future versions.

---

📜 License

This project is open-source.

See the repository license for the exact terms.

---

👤 Author

Created by KILLERDUTCH

GitHub:

https://github.com/KILLERDUTCH

---

<div align="center">CSS FORENSICS

Inspect. Detect. Understand.

Made with HTML, CSS & JavaScript.

</div>
