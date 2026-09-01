CSS Forensics

«A lightweight client-side CSS intelligence & forensic analysis toolkit.»

CSS Forensics analyzes raw CSS and turns it into a structured report that helps developers identify suspicious patterns, duplication, excessive overrides, high specificity, and other maintainability issues.

Built entirely with HTML, CSS, and Vanilla JavaScript — with no backend, dependencies, build tools, or installation required.

---

🌐 Live Demo

Try CSS Forensics directly in your browser:

"→ Launch CSS Forensics" (https://killerdutch.github.io/CSS-Forensics/)

«100% client-side: Your CSS is analyzed locally inside your browser and is never uploaded to a server.»

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
- Total findings

---

🚨 Forensic Risk Detection

CSS Forensics searches for patterns that may indicate maintainability problems.

Currently detects:

- Excessive "!important"
- Duplicate declarations
- Repeated property/value combinations
- High "z-index" values
- High selector specificity
- Deep selectors
- Large color systems
- Repeated CSS values

Findings are categorized by severity:

Severity| Meaning
🔴 "HIGH"| A potentially problematic pattern
🟡 "MEDIUM"| Something worth reviewing
🔵 "INFO"| Informational observation

---

🎨 Color Analysis

The analyzer extracts colors used throughout the stylesheet and calculates their frequency.

Supported formats include:

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
yellow
orange
purple
gray
grey
transparent

Example:

COLOR SYSTEM

#ffffff   ███████████████   12
#111111   ███████████        9
#6c5ce7   ██████             5
#ff4757   ███                3

This makes it easier to spot fragmented or unnecessarily large color systems.

---

📈 Property Frequency

CSS Forensics analyzes which CSS properties appear most frequently.

Example:

PROPERTY FREQUENCY

color        █████████████████   18
padding      ███████████         12
margin       █████████            9
background   ███████              7
display      █████                5

Useful for quickly understanding the structure and patterns of a stylesheet.

---

♻️ Duplicate Detection

CSS Forensics detects duplicate declarations inside CSS rules and repeated property/value combinations across rules.

Example:

.card {
    padding: 20px;
    padding: 20px;
}

The analyzer reports:

HIGH

Duplicate padding: 20px

Same declaration appears twice in one rule.

---

⚠️ "!important" Detection

"!important" isn't automatically bad, but excessive usage can make the CSS cascade harder to reason about.

Example:

.button {
    color: white !important;
}

.modal {
    z-index: 9999 !important;
}

CSS Forensics tracks these occurrences and reports them as forensic findings.

If the stylesheet contains heavy usage, it can also generate a global warning:

HIGH

Heavy !important usage

8 priority overrides detected.

---

🧱 High "z-index" Detection

Extremely large "z-index" values can be a sign of an uncontrolled stacking system.

Example:

.modal {
    z-index: 99999;
}

CSS Forensics flags values above the configured threshold:

MEDIUM

High z-index: 99999

Extremely high stacking value.

---

🎯 Specificity Analysis

CSS Forensics calculates selector specificity and flags selectors with unusually high specificity.

For example:

#app .page .content .sidebar .menu a.active {
    color: red;
}

The analyzer calculates a specificity score and reports potentially difficult-to-override selectors.

---

🪆 Deep Selector Detection

Deeply nested selectors can increase coupling and make styles harder to maintain.

Example:

.page .content .sidebar .menu ul li a span {
    color: white;
}

CSS Forensics detects selectors with excessive nesting depth and reports them for review.

---

🖥️ Interface

The interface is designed around a dark, technical developer-tool aesthetic.

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

The UI is:

- Dark themed
- Responsive
- Keyboard-friendly
- Dependency-free
- Built for developer workflows

---

🚀 Getting Started

CSS Forensics requires no Node.js, npm, server, or build process.

Clone the repository

git clone https://github.com/KILLERDUTCH/CSS-Forensics.git

Open the project

cd CSS-Forensics

Then simply open:

index.html

in your browser.

That's it.

---

🧩 Usage

1. Paste CSS

Paste your stylesheet into the editor.

body {
    margin: 0;
    color: #fff;
    background: #111;
}

2. Analyze

Click:

ANALYZE CSS

or use:

CTRL + ENTER

On macOS:

CMD + ENTER

3. Inspect the report

The dashboard generates:

- Stylesheet statistics
- Color analysis
- Risk signals
- Detailed findings
- Property frequency
- Specificity warnings
- Selector depth warnings

4. Export

Use:

EXPORT JSON

to export the analysis report as:

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
   └── Report Builder
   │
   ▼
FORENSIC REPORT

There is currently:

- ❌ No backend
- ❌ No database
- ❌ No account system
- ❌ No CSS upload service
- ❌ No analytics dependency
- ❌ No external framework

Your CSS does not need to leave your browser.

---

🧠 How It Works

The analyzer follows a lightweight processing pipeline:

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
    ├───────────────┤
    ▼
Specificity Analysis
    │
    ▼
Selector Depth Analysis
    │
    ▼
Risk Detection
    │
    ▼
Report Generation
    │
    ▼
Interactive Dashboard

The current implementation uses browser-side JavaScript with a lightweight parser and pattern-based analysis.

This keeps the project fast and dependency-free.

---

🛠️ Tech Stack

CSS Forensics intentionally avoids frameworks and external dependencies.

Core Technologies

- HTML5
- CSS3
- Vanilla JavaScript
- DOM APIs
- Blob API
- Browser APIs

Dependencies

0 npm packages
0 frameworks
0 build tools
0 backend services

---

📁 Project Structure

The application is intentionally contained in a single HTML file.

CSS-Forensics/
│
├── index.html
└── README.md

"index.html" contains:

HTML
│
├── Interface
│
├── CSS
│   └── Complete UI styling
│
└── JavaScript
    ├── CSS parser
    ├── Analyzer
    ├── Detectors
    ├── Report generator
    └── JSON exporter

This makes the project extremely easy to run, inspect, fork, and modify.

---

🧪 Example

Given this stylesheet:

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
    z-index: 99999;
}

CSS Forensics can produce findings such as:

HIGH
Duplicate padding: 20px

MEDIUM
High z-index: 9999

MEDIUM
High z-index: 99999

MEDIUM
!important used on background

MEDIUM
!important used on color

And statistics such as:

SELECTORS       3
DECLARATIONS    8
!IMPORTANT      2
DUPLICATES      1

---

📤 JSON Reports

Analysis results can be exported as JSON.

Example:

{
  "version": "1.0",
  "analyzedAt": "2026-09-01T00:00:00.000Z",
  "selectors": 3,
  "declarations": 8,
  "important": 2,
  "uniqueColors": 2,
  "properties": {
    "color": 2,
    "background": 2,
    "padding": 2,
    "z-index": 2
  },
  "colors": {
    "#ffffff": 2,
    "#111111": 2
  },
  "findings": []
}

The exported format can also serve as a foundation for future automation and integrations.

---

⌨️ Keyboard Shortcuts

Shortcut| Action
"CTRL + ENTER"| Analyze CSS
"CMD + ENTER"| Analyze CSS on macOS

---

📱 Responsive Design

CSS Forensics adapts to different screen sizes:

- Desktop
- Laptop
- Tablet
- Mobile

On smaller screens, the editor and analysis dashboard switch to a single-column layout.

---

🗺️ Roadmap

CSS Forensics is still evolving.

Current

- [x] CSS statistics
- [x] Selector counting
- [x] Declaration counting
- [x] "!important" detection
- [x] Duplicate detection
- [x] Repeated declaration detection
- [x] Color extraction
- [x] Color frequency analysis
- [x] Property frequency
- [x] High "z-index" detection
- [x] Specificity analysis
- [x] Deep selector detection
- [x] Risk signals
- [x] JSON export
- [x] Responsive interface

Planned

- [ ] Unused selector detection
- [ ] Duplicate selector detection
- [ ] CSS variable analysis
- [ ] CSS variable recommendations
- [ ] Shorthand property detection
- [ ] "@media" analysis
- [ ] "@supports" analysis
- [ ] "@layer" analysis
- [ ] "@keyframes" analysis
- [ ] Advanced value analysis
- [ ] CSS health score
- [ ] Before / after comparison
- [ ] Interactive specificity graph
- [ ] CSS cascade visualizer
- [ ] Advanced CSS parser
- [ ] CLI version
- [ ] GitHub Action

---

💡 Vision

CSS Forensics isn't intended to be another CSS formatter.

The goal is to build a lightweight CSS intelligence tool that helps developers understand what is happening inside a stylesheet.

Instead of only asking:

«"Is this CSS valid?"»

CSS Forensics focuses on questions like:

«"Where are the suspicious patterns?"»

«"Why is this stylesheet becoming difficult to maintain?"»

«"Which selectors deserve attention?"»

«"How consistent is this stylesheet?"»

«"Where is the cascade becoming unnecessarily complex?"»

That is the core idea behind CSS Forensics.

---

🤝 Contributing

Contributions, ideas, and improvements are welcome.

1. Fork the repository

2. Create a feature branch

git checkout -b feature/my-feature

3. Make your changes

4. Test the project locally

5. Commit your changes

git commit -m "Add my feature"

6. Push your branch

git push origin feature/my-feature

7. Open a Pull Request

For new detectors, please explain:

- What pattern is being detected
- Why it matters
- How it should be classified
- Example CSS
- Expected analyzer output

---

🐛 Issues

Found a bug?

Open an issue with:

- Browser
- Operating system
- CSS that reproduces the problem
- Expected behavior
- Actual behavior
- Screenshot, if useful

A minimal reproducible example is always appreciated.

---

⚠️ Limitations

CSS Forensics currently uses a lightweight browser-side parser rather than a complete CSS specification parser.

Because of this, some advanced or highly unusual CSS syntax may not be interpreted perfectly.

Examples include:

@supports (...) {
    ...
}

@media (...) {
    ...
}

@layer components {
    ...
}

Complex nested structures, unusual syntax, and edge cases may require a more advanced parser.

A more robust parsing engine is planned for future versions.

---

📄 License

This project is open source.

See the repository's "LICENSE" file for the exact license terms.

---

👤 Author

Created by KILLERDUTCH

GitHub:

https://github.com/KILLERDUTCH

---

<div align="center">CSS FORENSICS

Inspect. Detect. Understand.

Built with HTML, CSS & Vanilla JavaScript.

</div>
```
