# 🌱 Groot – A Lightweight Git-like Version Control System

Groot is a minimal yet functional version control system that allows you to `init`, `add`, `commit`, view `log`s, and even see `diff`s between commits — all without using Git. It operates using its own `.groot` directory to manage files, commits, and content snapshots.

---
## ✨ Features

- 🔧 Initialize a new `.groot` repository
- ➕ Add files to staging
- 📝 Commit changes with messages
- 🧾 View commit history (log)
- 🧩 View diffs between commits (with colored output)
- 🛑 Tracks parent commits like a linked list
- 🔐 Uses SHA-1 hashing for content IDs

---

## 🚀 Getting Started

### 1. Make the Script Executable

At the top of your `groot.mjs` file, ensure you have the following line to tell the system it's a Node.js executable:

```js
#!/usr/bin/env node

```

---

## 🛠️ Usage Commands

### 🔹 Add a file to staging

```bash
./groot.mjs add sample.txt
```

### 🔹 Commit changes

```bash
./groot.mjs commit "Initial commit"
```

### 🔹 View commit history
```bash
./groot.mjs log
```

### 🔹 Show file diffs for a specific commit


```bash
./groot.mjs show <commit_hash>
```

✅ Shows changes with colored output:

- 🟩 **Green** for additions  
- 🟥 **Red** for deletions  
- 🟨 **Yellow** for unchanged lines


---

## 🔍 Internals: How Groot Works

- **Staging Area**: Tracked in `.groot/index` as a JSON array of `{ path, hash }` objects.
- **Commits**: Stored in `.groot/objects/` as JSON blobs, each representing a snapshot of files and metadata.
- **Content Hashing**: Uses `SHA-1` (via Node.js `crypto` module) to uniquely identify file contents and commits.
- **HEAD**: The `.groot/HEAD` file always points to the latest commit’s hash.

---

## 🧠 Design Highlights

- No external dependencies for versioning logic — clean and modular.
- Custom object storage architecture (like Git’s blob model) using `objects/` folder.
- Recursive parent-pointer-based commit history for clean traversal and logging.
- File diffs are shown using colored terminal output via the `diff` and `chalk` libraries.

---

## 📦 Dependencies

Install the required dependencies with:

```bash
npm install chalk diff commander
```

