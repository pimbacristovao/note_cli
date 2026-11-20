# 📝 Note CLI

<div align="center">

**A command-line note manager built with Node.js**

*A learning project for creating, searching, listing, and removing notes from the terminal*

[![Node.js](https://img.shields.io/badge/Node.js-ESM-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Yargs](https://img.shields.io/badge/Yargs-CLI-8A2BE2?style=flat-square)](https://yargs.js.org/)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](#-license)

</div>

## 🎯 Project Overview

Note CLI is a small command-line application for managing notes locally. Notes are stored in a JSON file and can be created, listed, searched, removed, or displayed in a browser.

The project demonstrates:

- **CLI development** with Node.js and `yargs`
- **ES modules** with native `import`/`export`
- **JSON persistence** using the Node.js file system API
- **A simple HTTP server** for viewing notes in a browser
- **Automated tests** with Jest

---

## 📋 Table of Contents

<details>
<summary><strong>🛠️ Technology Stack</strong></summary>

- **Node.js** - JavaScript runtime
- **Yargs** - Command-line argument parsing
- **Open** - Opens the notes page in the default browser
- **Jest** - Testing framework
- **JSON** - Local data persistence

</details>

<details>
<summary><strong>🚀 Quick Start Guide</strong></summary>

### Prerequisites

- **Node.js** installed
- **npm** installed

### Installation

```bash
# Enter the project directory
cd cli_project

# Install dependencies
npm install
```

The CLI is exposed locally as the `note` command through the `bin` configuration in `package.json`.

### Create and list notes

```bash
# Create a note
npm exec note -- new "Study Node.js"

# Create a note with comma-separated tags
npm exec note -- new "Practice CLI commands" --tags node,cli

# List all notes
npm exec note -- all
```

</details>

<details>
<summary><strong>📁 Project Structure</strong></summary>

```text
cli_project/
├── index.js             # CLI entry point
├── package.json         # Project metadata, scripts, and CLI configuration
├── db.json              # Local notes database
├── src/
│   ├── command.js       # CLI commands and argument parsing
│   ├── db.js            # JSON database read/write operations
│   ├── notes.js         # Note management operations
│   ├── server.js        # HTTP server for the web view
│   └── template.html    # HTML template used by the web view
└── tests/
    └── notes.test.js    # Note operations tests
```

</details>

<details>
<summary><strong>🌟 Features and Commands</strong></summary>

| Command | Description |
|---------|-------------|
| `new <note>` | Creates a note |
| `all` | Lists all notes |
| `find <filter>` | Finds notes whose content contains the search term |
| `remove <id>` | Removes a note by its numeric ID |
| `clean` | Removes all notes |
| `web [port]` | Starts a web view on port `5000` by default |

### Tags

Tags can be added when creating a note with `--tags` or its `-t` alias:

```bash
npm exec note -- new "Read about HTTP servers" -t node,http
```

### Searching

Search is case-insensitive and is applied to the note content:

```bash
npm exec note -- find node
```

### Removing notes

Use the ID shown by the `all` command:

```bash
npm exec note -- remove 1712345678901
npm exec note -- clean
```

</details>

<details>
<summary><strong>🌐 Web View</strong></summary>

The `web` command starts a local HTTP server, renders the current notes using `src/template.html`, and opens the page in the default browser.

```bash
# Use the default port (5000)
npm exec note -- web

# Use a custom port
npm exec note -- web 8080
```

Open the page manually at [http://localhost:5000](http://localhost:5000) when using the default port.

</details>

<details>
<summary><strong>💾 Data Persistence</strong></summary>

Notes are saved in [`db.json`](./db.json) in the following format:

```json
{
  "notes": [
    {
      "id": 1712345678901,
      "content": "Study Node.js",
      "tags": ["node", "learning"]
    }
  ]
}
```

The database is read and written by [`src/db.js`](./src/db.js). The file is local to this project and does not require an external database.

</details>

<details>
<summary><strong>🧪 Development and Testing</strong></summary>

### Run the tests

```bash
npm test
```

### Run the CLI directly

```bash
node index.js all
```

The CLI entry point is [`index.js`](./index.js), while command definitions are implemented in [`src/command.js`](./src/command.js).

</details>

---

## 🤝 Contributing

This is a learning project. Suggestions, bug reports, and improvements are welcome.

## 📄 License

This project is available under the MIT License, as declared in `package.json`.

---

<div align="center">

**Built with Node.js for learning and experimentation**

</div>