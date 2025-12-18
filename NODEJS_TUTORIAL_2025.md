# 🚀 Node.js Complete Mastery 2025 - Beginner to Advanced

> **The ultimate guide to mastering Node.js - from first principles to production-ready applications**

**Version:** 2025.1  
**Node.js Version:** v25.x (Current) | v24.x (LTS)  
**Last Updated:** December 2025

---

## 📖 How to Use This Tutorial

This tutorial is designed for **progressive learning**:
- ✅ **Beginners**: Start from Chapter 1
- ✅ **Intermediate**: Jump to Chapter 6
- ✅ **Advanced**: Focus on Chapters 16-22
- ✅ **Quick Reference**: Use Table of Contents

**Recommended Learning Path:**
1. Read the concept
2. Type out the examples (don't copy-paste!)
3. Modify examples to test understanding
4. Build the practice projects
5. Review after 24 hours (reinforcement)

---

## 📚 Complete Table of Contents

### 🌟 PART 1: FOUNDATIONS (Chapters 1-5)
1. [What is Node.js?](#1--what-is-nodejs)
2. [Installation & Environment Setup](#2--installation--environment-setup)
3. [Your First Node.js Programs](#3--your-first-nodejs-programs)
4. [Understanding JavaScript Runtime](#4--understanding-javascript-runtime)
5. [Node.js Architecture Deep Dive](#5--nodejs-architecture-deep-dive)

### 📦 PART 2: CORE CONCEPTS (Chapters 6-10)
6. [Modules & Module System](#6--modules--module-system)
7. [npm & Package Management](#7--npm--package-management)
8. [Asynchronous Programming Mastery](#8--asynchronous-programming-mastery)
9. [The Event Loop in Detail](#9--the-event-loop-in-detail)
10. [Streams & Buffers](#10--streams--buffers)

### 🔧 PART 3: BUILT-IN MODULES (Chapters 11-15)
11. [File System Operations](#11--file-system-operations)
12. [HTTP & HTTPS Modules](#12--http--https-modules)
13. [Path, URL & Query Strings](#13--path-url--query-strings)
14. [Events & EventEmitter Pattern](#14--events--eventemitter-pattern)
15. [Process, OS & Child Processes](#15--process-os--child-processes)

### 🚀 PART 4: WEB DEVELOPMENT (Chapters 16-18)
16. [Express.js Framework](#16--expressjs-framework)
17. [REST API Development](#17--rest-api-development)
18. [Template Engines & Server-Side Rendering](#18--template-engines--server-side-rendering)

### 💾 PART 5: DATABASES & PERSISTENCE (Chapters 19-20)
19. [Working with MongoDB](#19--working-with-mongodb)
20. [SQL Databases (PostgreSQL/MySQL)](#20--sql-databases-postgresqlmysql)

### 🔐 PART 6: SECURITY & AUTHENTICATION (Chapters 21-22)
21. [Security Best Practices](#21--security-best-practices)
22. [Authentication & Authorization](#22--authentication--authorization)

### ✅ PART 7: TESTING & QUALITY (Chapters 23-24)
23. [Testing with Jest](#23--testing-with-jest)
24. [Error Handling & Debugging](#24--error-handling--debugging)

### ⚡ PART 8: ADVANCED TOPICS (Chapters 25-28)
25. [Performance Optimization](#25--performance-optimization)
26. [Clustering & Load Balancing](#26--clustering--load-balancing)
27. [WebSockets & Real-Time Apps](#27--websockets--real-time-apps)
28. [Microservices Architecture](#28--microservices-architecture)

### 🚢 PART 9: DEPLOYMENT & PRODUCTION (Chapters 29-30)
29. [Docker & Containerization](#29--docker--containerization)
30. [Production Deployment & DevOps](#30--production-deployment--devops)

---

# 🌟 PART 1: FOUNDATIONS

## 1. 🎯 What is Node.js?

### The Elevator Pitch

**Node.js is a JavaScript runtime built on Chrome's V8 engine that lets you run JavaScript outside the browser.**

Before Node.js (2009), JavaScript only lived in browsers. Ryan Dahl changed that forever.

### The Real Definition

```
┌─────────────────────────────────────────────────────┐
│                    NODE.JS                          │
├─────────────────────────────────────────────────────┤
│  • JavaScript Runtime Environment                   │
│  • Built on Chrome V8 Engine                        │
│  • Asynchronous & Event-Driven                      │
│  • Single-Threaded with Event Loop                  │
│  • Cross-Platform (Windows, macOS, Linux)           │
│  • Open Source (maintained by OpenJS Foundation)    │
└─────────────────────────────────────────────────────┘
```

### Why Node.js Exists

**The Problem Node.js Solved:**

Traditional web servers (Apache, PHP) used **one thread per connection**:
```
Request 1 → Thread 1 → [WAIT for database] → Response
Request 2 → Thread 2 → [WAIT for file I/O] → Response
Request 3 → Thread 3 → [WAIT for API call] → Response
...
Request 1000 → Thread 1000 → 💥 Server crashes
```

**Node.js Solution - Event-Driven Architecture:**
```
Request 1 → [start DB query] ────┐
Request 2 → [start file read] ────┤
Request 3 → [start API call] ─────┼─→ One Thread + Event Loop
Request 4 → [start process] ──────┤
...                                │
Request 1000 → [immediate start] ─┘
              ↓
      [Callbacks execute when ready]
```

### Key Characteristics

#### 1. **Asynchronous & Non-Blocking**

```javascript
// Traditional (Blocking)
const data = readFileSync('large.txt'); // STOPS HERE
console.log(data);
console.log('Next task'); // Waits

// Node.js (Non-Blocking)
readFile('large.txt', (data) => {
  console.log(data);
});
console.log('Next task'); // Runs immediately!
```

#### 2. **Event-Driven Architecture**

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

// Register listener
emitter.on('userLoggedIn', (username) => {
  console.log(`Welcome ${username}!`);
  sendEmail(username);
  logActivity(username);
});

// Trigger event
emitter.emit('userLoggedIn', 'alice');
```

#### 3. **Single-Threaded (But Scalable)**

```
┌─────────────────────────────────────────┐
│       Your JavaScript Code              │
│      (Single Thread - Main)             │
└──────────────┬──────────────────────────┘
               │
        ┌──────▼──────┐
        │  Event Loop │
        └──────┬──────┘
               │
    ┌──────────┴─────────────┐
    │                        │
    ▼                        ▼
┌──────────────┐    ┌───────────────────┐
│  libuv       │    │   Worker Pool     │
│  (I/O Poll)  │    │  (4-128 threads)  │
└──────────────┘    └───────────────────┘
    │                        │
    └────────────┬───────────┘
                 ▼
         ┌───────────────┐
         │ OS Operations │
         └───────────────┘
```

### What Node.js is Perfect For

✅ **Excellent Use Cases:**

**1. REST APIs & Microservices**
```javascript
// High-throughput API server
app.get('/api/users', async (req, res) => {
  const users = await db.query('SELECT * FROM users');
  res.json(users);
});
// Handles thousands of concurrent requests
```

**2. Real-Time Applications**
- Chat applications (Slack, Discord)
- Collaboration tools (Google Docs)
- Live dashboards
- Multiplayer games

**3. Streaming Applications**
- Video/audio streaming (Netflix uses Node.js)
- File upload/download
- Data processing pipelines

**4. Server-Side Rendering (SSR)**
- Next.js applications
- Nuxt.js applications
- Dynamic content generation

**5. Command-Line Tools**
- Build tools (Webpack, Vite)
- Development tools (ESLint, Prettier)
- System utilities

**6. IoT Applications**
- Sensor data collection
- Device control systems
- Edge computing

❌ **Not Ideal For:**

**1. CPU-Intensive Tasks**
```javascript
// ❌ Bad: Blocks event loop
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
const result = fibonacci(45); // Blocks for seconds!
```

**2. Heavy Computation**
- Video encoding
- Image processing (at scale)
- Machine learning training
- Scientific computing

**Better alternatives:** Python, Go, Rust, C++

### Real-World Success Stories

#### **Netflix**
- **Challenge:** 40-minute startup time
- **Solution:** Migrated to Node.js
- **Result:** 70% faster startup, better performance

#### **PayPal**
- **Challenge:** Java-based monolith
- **Solution:** Rebuilt with Node.js
- **Result:** Built 2x faster, 33% fewer lines of code, 2x faster response time

#### **Uber**
- **Challenge:** Scaling ride-matching system
- **Solution:** Node.js microservices
- **Result:** Handles millions of rides daily

#### **NASA**
- **Challenge:** Keep astronauts safe with real-time data
- **Solution:** Node.js for data processing
- **Result:** Lives saved through faster response times

### Node.js Ecosystem

```
                    Node.js Ecosystem
                           │
           ┌───────────────┼───────────────┐
           │               │               │
      ┌────▼────┐    ┌─────▼─────┐   ┌────▼────┐
      │   npm   │    │ Libraries  │   │  Tools  │
      │ 2M pkgs │    │  Express   │   │  Jest   │
      └─────────┘    │  React     │   │ Webpack │
                     │  Vue       │   │ ESLint  │
                     └────────────┘   └─────────┘
```

**npm (Node Package Manager):**
- 2+ million packages
- Largest software registry in the world
- 100+ billion downloads per month

### Understanding the Runtime

```javascript
// This is JavaScript (the language)
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);

// This is Node.js (the runtime)
const fs = require('fs');          // File system access
const http = require('http');      // HTTP server
const crypto = require('crypto');  // Cryptography

// Browser APIs (not in Node.js)
// document.querySelector()        // ❌ Not available
// window.location                 // ❌ Not available
// localStorage                    // ❌ Not available

// Node.js APIs (not in browsers)
// require()                       // ✅ Node.js only
// process.env                     // ✅ Node.js only
// __dirname                       // ✅ Node.js only
```

---

## 2. 🔧 Installation & Environment Setup

### Understanding Node.js Versions

**Release Schedule:**
```
October:  Odd version (25.x)  → Current (6 months)
April:    Even version (24.x) → Current → LTS (30 months)
```

**Which Version to Use?**

- **v24.x (LTS)** ← Recommended for production
  - Long-term support until October 2027
  - Stable and tested
  - Security updates guaranteed

- **v25.x (Current)** ← Latest features
  - Cutting-edge features
  - For experimentation
  - Becomes LTS in April 2026

### Installation Methods

#### Method 1: Official Installer (Beginners)

**Step 1:** Visit [nodejs.org](https://nodejs.org)

**Step 2:** Download installer
- **LTS (Long Term Support)** - Recommended
- **Current** - Latest features

**Step 3:** Run installer
- Windows: `.msi` installer
- macOS: `.pkg` installer
- Linux: Use package manager

**Step 4:** Verify installation
```bash
node --version
# Should output: v24.x.x or v25.x.x

npm --version
# Should output: 10.x.x
```

#### Method 2: nvm (Node Version Manager) - Recommended

**Why nvm?**
- Switch between Node versions instantly
- Test code on different versions
- Different projects can use different versions

**Install nvm:**

**macOS/Linux:**
```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Or with wget
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Restart terminal or run:
source ~/.bashrc  # or ~/.zshrc

# Verify
nvm --version
```

**Windows:**
Download **nvm-windows** from:
https://github.com/coreybutler/nvm-windows/releases

**Using nvm:**
```bash
# List available versions
nvm list available

# Install latest LTS
nvm install --lts
nvm install 24

# Install latest current
nvm install node
nvm install 25

# Install specific version
nvm install 24.1.0

# List installed versions
nvm list

# Switch version
nvm use 24

# Set default version
nvm alias default 24

# Check current version
node --version
```

#### Method 3: Package Managers

**macOS (Homebrew):**
```bash
# Install Homebrew first
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Node.js
brew install node

# Install specific version
brew install node@24

# Update
brew upgrade node
```

**Ubuntu/Debian:**
```bash
# Using NodeSource repository (recommended)
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify
node --version
npm --version
```

**Windows (Chocolatey):**
```bash
# Install Chocolatey first (as Administrator)
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Install Node.js
choco install nodejs

# Install specific version
choco install nodejs --version=24.1.0
```

**Windows (Scoop):**
```bash
# Install Scoop first
iwr -useb get.scoop.sh | iex

# Install Node.js
scoop install nodejs

# Install LTS version
scoop install nodejs-lts
```

### Setting Up Development Environment

#### 1. **Choose Your IDE**

**VS Code (Recommended)**
- Free and open-source
- Excellent Node.js support
- Huge extension ecosystem
- Download: https://code.visualstudio.com

**WebStorm**
- Professional IDE by JetBrains
- Powerful features
- Paid (but free for students)
- Download: https://www.jetbrains.com/webstorm

**Alternatives:**
- Sublime Text (lightweight)
- Atom (discontinued but still works)
- Vim/Neovim (for terminal lovers)

#### 2. **Essential VS Code Extensions**

```bash
# Install from VS Code marketplace or terminal:
code --install-extension dbaeumer.vscode-eslint
code --install-extension esbenp.prettier-vscode
code --install-extension christian-kohler.npm-intellisense
code --install-extension ms-vscode.vscode-typescript-next
code --install-extension PKief.material-icon-theme
code --install-extension ritwickdey.LiveServer
code --install-extension eamodio.gitlens
```

**Must-Have Extensions:**
1. **ESLint** - Code quality and error checking
2. **Prettier** - Code formatting
3. **npm Intellisense** - Autocomplete npm modules
4. **REST Client** - Test APIs without Postman
5. **GitLens** - Enhanced Git capabilities
6. **Path Intellisense** - Autocomplete file paths
7. **Thunder Client** - API testing
8. **Error Lens** - Inline error messages

#### 3. **Configure VS Code Settings**

Create `.vscode/settings.json` in your project:
```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "javascript.preferences.quoteStyle": "single",
  "typescript.preferences.quoteStyle": "single",
  "files.eol": "\n",
  "editor.tabSize": 2
}
```

#### 4. **Global npm Packages**

```bash
# Install useful global packages
npm install -g nodemon      # Auto-restart on file changes
npm install -g pm2          # Production process manager
npm install -g typescript   # TypeScript compiler
npm install -g ts-node      # Execute TypeScript directly
npm install -g npm-check-updates  # Update dependencies
npm install -g http-server  # Simple HTTP server
npm install -g eslint       # JavaScript linter

# Verify installations
nodemon --version
pm2 --version
tsc --version
```

#### 5. **Project Structure Setup**

```bash
# Create project directory
mkdir my-nodejs-project
cd my-nodejs-project

# Initialize Node.js project
npm init -y

# Create basic structure
mkdir src
mkdir tests
mkdir config
touch src/index.js
touch .gitignore
touch .env
touch README.md

# Initialize Git
git init
```

**Basic `.gitignore`:**
```gitignore
# Dependencies
node_modules/

# Environment variables
.env
.env.local
.env.production

# Logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*
*.log

# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo

# Build outputs
dist/
build/
coverage/

# Temporary files
tmp/
temp/
```

#### 6. **Environment Variables Setup**

Install dotenv:
```bash
npm install dotenv
```

Create `.env`:
```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp
DB_USER=admin
DB_PASSWORD=secret123

# API Keys
API_KEY=your_api_key_here
JWT_SECRET=your_secret_key_here
```

Use in code:
```javascript
// Load at the very top of your main file
require('dotenv').config();

const PORT = process.env.PORT || 3000;
const DB_HOST = process.env.DB_HOST;

console.log(`Server running on port ${PORT}`);
```

---

## 3. 👋 Your First Node.js Programs

### Program 1: Hello World

Create `hello.js`:
```javascript
// hello.js - Your first Node.js program
console.log('Hello, Node.js!');
console.log('Welcome to the world of server-side JavaScript');
```

Run it:
```bash
node hello.js
```

Output:
```
Hello, Node.js!
Welcome to the world of server-side JavaScript
```

**What just happened?**
1. Node.js read your file
2. V8 engine compiled JavaScript to machine code
3. Executed the code
4. Printed to console (stdout)
5. Process exited with code 0 (success)

### Program 2: Variables and Data Types

Create `variables.js`:
```javascript
// variables.js - Understanding JavaScript in Node.js

// Variables (ES6+)
const name = 'Alice';        // const: cannot reassign
let age = 30;                // let: can reassign
var city = 'New York';       // var: old way (avoid)

// Data Types
const string = 'Hello';
const number = 42;
const boolean = true;
const nullValue = null;
const undefinedValue = undefined;
const object = { key: 'value' };
const array = [1, 2, 3, 4, 5];
const func = function() { return 'I am a function'; };

// Template Literals
console.log(`${name} is ${age} years old and lives in ${city}`);

// Objects
const person = {
  name: 'Bob',
  age: 25,
  email: 'bob@example.com',
  greet: function() {
    return `Hello, I'm ${this.name}`;
  }
};

console.log(person.greet());

// Arrays
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);
const sum = numbers.reduce((acc, n) => acc + n, 0);

console.log('Doubled:', doubled);
console.log('Sum:', sum);

// Destructuring
const { name: personName, age: personAge } = person;
const [first, second, ...rest] = numbers;

console.log(personName, personAge);
console.log(first, second, rest);
```

### Program 3: Functions

Create `functions.js`:
```javascript
// functions.js - Different ways to write functions

// 1. Function Declaration
function add(a, b) {
  return a + b;
}

// 2. Function Expression
const subtract = function(a, b) {
  return a - b;
};

// 3. Arrow Function
const multiply = (a, b) => a * b;

// 4. Arrow Function with Block
const divide = (a, b) => {
  if (b === 0) {
    throw new Error('Division by zero!');
  }
  return a / b;
};

// Higher-Order Functions
function calculate(operation, a, b) {
  return operation(a, b);
}

console.log(calculate(add, 10, 5));      // 15
console.log(calculate(multiply, 10, 5)); // 50

// Callback Functions
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, name: 'User' };
    callback(data);
  }, 1000);
}

fetchData((data) => {
  console.log('Data received:', data);
});

// Promises
function fetchDataPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve({ id: 1, name: 'User' });
    }, 1000);
  });
}

fetchDataPromise()
  .then(data => console.log('Promise data:', data))
  .catch(error => console.error(error));

// Async/Await
async function fetchDataAsync() {
  try {
    const data = await fetchDataPromise();
    console.log('Async data:', data);
  } catch (error) {
    console.error(error);
  }
}

fetchDataAsync();
```

### Program 4: Your First Web Server

Create `server.js`:
```javascript
// server.js - Simple HTTP server
const http = require('http');

// Create server
const server = http.createServer((req, res) => {
  // Set response headers
  res.writeHead(200, { 
    'Content-Type': 'text/html',
    'X-Powered-By': 'Node.js'
  });
  
  // Handle different routes
  if (req.url === '/') {
    res.end('<h1>Welcome to Node.js Server!</h1>');
  } else if (req.url === '/about') {
    res.end('<h1>About Page</h1><p>This is a Node.js server</p>');
  } else if (req.url === '/api/data') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Hello from API', timestamp: Date.now() }));
  } else {
    res.writeHead(404, { 'Content-Type': 'text/html' });
    res.end('<h1>404 - Page Not Found</h1>');
  }
});

// Start server
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}/`);
  console.log('Press Ctrl+C to stop');
});
```

Run it:
```bash
node server.js
```

Visit in browser:
- http://localhost:3000/
- http://localhost:3000/about
- http://localhost:3000/api/data

### Program 5: File Operations

Create `files.js`:
```javascript
// files.js - Reading and writing files
const fs = require('fs');

// 1. Write to file (asynchronous)
const content = 'Hello from Node.js!\nThis is a new line.';

fs.writeFile('output.txt', content, (err) => {
  if (err) {
    console.error('Error writing file:', err);
    return;
  }
  console.log('File written successfully!');
});

// 2. Read from file (asynchronous)
fs.readFile('output.txt', 'utf8', (err, data) => {
  if (err) {
    console.error('Error reading file:', err);
    return;
  }
  console.log('File content:', data);
});

// 3. Append to file
fs.appendFile('output.txt', '\nAppended line', (err) => {
  if (err) {
    console.error('Error appending:', err);
    return;
  }
  console.log('Content appended!');
});

// 4. Check if file exists
fs.access('output.txt', fs.constants.F_OK, (err) => {
  console.log(err ? 'File does not exist' : 'File exists');
});

// 5. Delete file
fs.unlink('output.txt', (err) => {
  if (err) {
    console.error('Error deleting file:', err);
    return;
  }
  console.log('File deleted!');
});

// Synchronous versions (use sparingly!)
try {
  fs.writeFileSync('sync-output.txt', 'Synchronous write');
  const syncData = fs.readFileSync('sync-output.txt', 'utf8');
  console.log('Sync read:', syncData);
} catch (err) {
  console.error('Sync error:', err);
}
```

### Program 6: Interactive Console App

Create `interactive.js`:
```javascript
// interactive.js - CLI application with user input
const readline = require('readline');

// Create interface
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

// Simple calculator
function calculator() {
  rl.question('Enter first number: ', (num1) => {
    rl.question('Enter operator (+, -, *, /): ', (operator) => {
      rl.question('Enter second number: ', (num2) => {
        const n1 = parseFloat(num1);
        const n2 = parseFloat(num2);
        let result;

        switch (operator) {
          case '+':
            result = n1 + n2;
            break;
          case '-':
            result = n1 - n2;
            break;
          case '*':
            result = n1 * n2;
            break;
          case '/':
            result = n1 / n2;
            break;
          default:
            console.log('Invalid operator!');
            rl.close();
            return;
        }

        console.log(`Result: ${n1} ${operator} ${n2} = ${result}`);
        
        rl.question('Calculate again? (y/n): ', (answer) => {
          if (answer.toLowerCase() === 'y') {
            calculator();
          } else {
            console.log('Goodbye!');
            rl.close();
          }
        });
      });
    });
  });
}

console.log('=== Node.js Calculator ===');
calculator();
```

### Program 7: Command-Line Arguments

Create `args.js`:
```javascript
// args.js - Working with command-line arguments
console.log('Process arguments:', process.argv);

// process.argv structure:
// [0] - Node executable path
// [1] - Script file path
// [2+] - Your arguments

const args = process.argv.slice(2);

if (args.length === 0) {
  console.log('No arguments provided');
  console.log('Usage: node args.js <name> <age>');
  process.exit(1);
}

const [name, age] = args;
console.log(`Hello ${name}, you are ${age} years old`);

// Advanced argument parsing
const options = {};
for (let i = 0; i < args.length; i += 2) {
  const key = args[i].replace('--', '');
  const value = args[i + 1];
  options[key] = value;
}

console.log('Parsed options:', options);
```

Run it:
```bash
node args.js Alice 30
node args.js --name Bob --age 25 --city NYC
```

### Program 8: Environment Variables

Create `env.js`:
```javascript
// env.js - Working with environment variables
console.log('Node Version:', process.version);
console.log('Platform:', process.platform);
console.log('Architecture:', process.arch);
console.log('Current Directory:', process.cwd());
console.log('Process ID:', process.pid);

// Environment variables
console.log('\nEnvironment Variables:');
console.log('NODE_ENV:', process.env.NODE_ENV || 'development');
console.log('USER:', process.env.USER);
console.log('HOME:', process.env.HOME);

// Custom environment variables
// Set them before running: PORT=8000 node env.js
const PORT = process.env.PORT || 3000;
console.log(`Server will run on port ${PORT}`);

// Exit codes
process.on('exit', (code) => {
  console.log(`About to exit with code: ${code}`);
});

// Graceful shutdown
process.on('SIGINT', () => {
  console.log('\nReceived SIGINT. Graceful shutdown...');
  // Clean up resources here
  process.exit(0);
});

console.log('\nPress Ctrl+C to exit');
```

Run it:
```bash
node env.js
PORT=8000 NODE_ENV=production node env.js
```

---

## 4. 🧠 Understanding JavaScript Runtime

### The JavaScript Engine (V8)

Node.js uses **V8**, the same engine that powers Google Chrome.

```
┌──────────────────────────────────────┐
│           YOUR CODE                  │
│        (JavaScript)                  │
└────────────┬─────────────────────────┘
             │
             ▼
┌──────────────────────────────────────┐
│         V8 ENGINE                    │
│                                      │
│  ┌────────────────────────────┐    │
│  │      Parser                │    │
│  │  (Code → AST)              │    │
│  └────────┬───────────────────┘    │
│           │                         │
│           ▼                         │
│  ┌────────────────────────────┐    │
│  │   Ignition Interpreter     │    │
│  │  (AST → Bytecode)          │    │
│  └────────┬───────────────────┘    │
│           │                         │
│           ▼                         │
│  ┌────────────────────────────┐    │
│  │  TurboFan Compiler         │    │
│  │  (Hot Code → Machine Code) │    │
│  └────────┬───────────────────┘    │
└───────────┼─────────────────────────┘
            │
            ▼
    ┌──────────────────┐
    │  Machine Code    │
    │  (CPU executes)  │
    └──────────────────┘
```

**V8's Process:**

1. **Parse**: Source code → Abstract Syntax Tree (AST)
2. **Interpret**: AST → Bytecode (Ignition)
3. **Execute**: Run bytecode
4. **Optimize**: Hot code → Optimized machine code (TurboFan)

**Why V8 is Fast:**
- Just-In-Time (JIT) compilation
- Inline caching
- Hidden classes for objects
- Efficient garbage collection

### Memory Management

#### Heap vs Stack

```javascript
// Stack Memory (Primitive values)
function calculate() {
  const x = 5;           // Stack
  const y = 10;          // Stack
  const result = x + y;  // Stack
  return result;
} // All cleaned up automatically when function returns

// Heap Memory (Objects and complex data)
const user = {           // Reference on stack, data on heap
  name: 'Alice',
  email: 'alice@example.com',
  posts: new Array(1000000)  // Large data on heap
};

const numbers = [1, 2, 3]; // Array on heap
```

**Memory Layout:**
```
┌─────────────────────────────────────┐
│          STACK                      │
│  (Function calls, primitives)       │
│                                     │
│  ┌─────────────────┐               │
│  │ x = 5           │               │
│  │ y = 10          │               │
│  │ user = <ref>    │───┐           │
│  └─────────────────┘   │           │
└─────────────────────────┼───────────┘
                          │
┌─────────────────────────▼───────────┐
│          HEAP                        │
│  (Objects, arrays, functions)       │
│                                      │
│  ┌────────────────────────────┐    │
│  │ { name: 'Alice',           │    │
│  │   email: '...',            │    │
│  │   posts: [...]  }          │    │
│  └────────────────────────────┘    │
└──────────────────────────────────────┘
```

#### Garbage Collection

V8 uses **generational garbage collection**:

```
┌────────────────────────────────────────┐
│        V8 HEAP                         │
│                                        │
│  ┌──────────────────────────────────┐ │
│  │   New Space (Young Generation)   │ │
│  │   - Recently created objects     │ │
│  │   - Fast, frequent collection    │ │
│  │   - Most objects die young       │ │
│  └──────────┬───────────────────────┘ │
│             │ (Survivors)             │
│             ▼                         │
│  ┌──────────────────────────────────┐ │
│  │   Old Space (Old Generation)     │ │
│  │   - Long-lived objects           │ │
│  │   - Slower, less frequent        │ │
│  └──────────────────────────────────┘ │
└────────────────────────────────────────┘
```

**Memory Leaks to Avoid:**

```javascript
// ❌ Memory leak: Global variables
global.leakyData = new Array(1000000);

// ❌ Memory leak: Forgotten timers
setInterval(() => {
  const data = new Array(1000);
  // Timer keeps running, data accumulates
}, 100);

// ❌ Memory leak: Closures holding references
function createClosure() {
  const largeData = new Array(1000000);
  return function() {
    // largeData is kept in memory
    return largeData[0];
  };
}

// ✅ Good: Clear intervals when done
const interval = setInterval(() => { }, 1000);
clearInterval(interval);

// ✅ Good: Don't keep unnecessary references
function processData() {
  let data = new Array(1000000);
  // Use data
  data = null; // Explicitly release
}
```

### Memory Limits

```bash
# Check default limit
node -e "console.log(v8.getHeapStatistics())"

# Increase heap size (to 4GB)
node --max-old-space-size=4096 app.js

# Decrease heap size (to 512MB)
node --max-old-space-size=512 app.js
```

### Global Objects

```javascript
// Global namespace
console.log(global);  // Global object

// Process information
console.log(process.version);     // v25.1.0
console.log(process.platform);    // linux, darwin, win32
console.log(process.arch);        // x64, arm64
console.log(process.pid);         // Process ID
console.log(process.ppid);        // Parent process ID
console.log(process.cwd());       // Current working directory
console.log(process.execPath);    // Path to Node executable

// Environment variables
console.log(process.env.NODE_ENV);
console.log(process.env.PATH);

// Command-line arguments
console.log(process.argv);

// __dirname and __filename
console.log(__dirname);  // /Users/you/project
console.log(__filename); // /Users/you/project/app.js

// require function
const fs = require('fs');

// module and exports
console.log(module);
console.log(module.exports === exports); // true

// Timers
setTimeout(() => console.log('timeout'), 1000);
setInterval(() => console.log('interval'), 1000);
setImmediate(() => console.log('immediate'));

// Buffer (for binary data)
const buf = Buffer.from('Hello');
console.log(buf); // <Buffer 48 65 6c 6c 6f>

// Console
console.log('log');
console.error('error');
console.warn('warning');
console.info('info');
console.debug('debug');
console.table([{ name: 'Alice' }, { name: 'Bob' }]);
console.time('operation');
// ... operation
console.timeEnd('operation');
```

### Understanding 'this' in Node.js

```javascript
// In global scope
console.log(this);  // {} (empty object in module)
console.log(this === module.exports);  // true

// In functions
function regularFunction() {
  console.log(this);  // global object or undefined (strict mode)
}

const arrowFunction = () => {
  console.log(this);  // Lexical this (from surrounding scope)
};

// In objects
const obj = {
  name: 'Object',
  regularMethod: function() {
    console.log(this);  // obj
  },
  arrowMethod: () => {
    console.log(this);  // Module's this (not obj)
  }
};
```

---

## 5. 🏗️ Node.js Architecture Deep Dive

### The Complete Picture

```
┌─────────────────────────────────────────────────────────────┐
│                   YOUR APPLICATION                          │
│                  (JavaScript Code)                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   NODE.JS CORE                              │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐ │
│  │               V8 JavaScript Engine                   │ │
│  │  • Compiles JS to machine code                       │ │
│  │  • Manages memory (heap & stack)                     │ │
│  │  • Executes JavaScript                               │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐ │
│  │              Node.js Bindings (C++)                  │ │
│  │  • Connect JavaScript to C++ libraries               │ │
│  │  • Wrap system calls                                 │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐ │
│  │                   libuv                              │ │
│  │                                                       │ │
│  │  ┌─────────────────────────────────────────────┐   │ │
│  │  │            EVENT LOOP                       │   │ │
│  │  │                                             │   │ │
│  │  │  ┌──────────┐  ┌────────┐  ┌──────────┐  │   │ │
│  │  │  │ Timers   │→ │  Poll  │→ │  Check   │  │   │ │
│  │  │  └──────────┘  └────────┘  └──────────┘  │   │ │
│  │  │       ↑                          │        │   │ │
│  │  │       └──────────────────────────┘        │   │ │
│  │  └─────────────────────────────────────────────┘   │ │
│  │                                                       │ │
│  │  ┌─────────────────────────────────────────────┐   │ │
│  │  │          THREAD POOL                        │   │ │
│  │  │  (4 threads by default, max 128)            │   │ │
│  │  │                                             │   │ │
│  │  │  • File I/O (fs operations)                 │   │ │
│  │  │  • DNS lookups (dns.lookup)                 │   │ │
│  │  │  • Crypto operations (pbkdf2, randomBytes)  │   │ │
│  │  │  • Compression (zlib)                       │   │ │
│  │  └─────────────────────────────────────────────┘   │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐ │
│  │          Other C/C++ Dependencies                    │ │
│  │  • c-ares (DNS resolution)                           │ │
│  │  • OpenSSL (Crypto, TLS/SSL)                         │ │
│  │  • http-parser (HTTP parsing)                        │ │
│  │  • zlib (Compression)                                │ │
│  └──────────────────────────────────────────────────────┘ │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              OPERATING SYSTEM                               │
│  • File System                                              │
│  • Network Stack                                            │
│  • Process Management                                       │
│  • System Calls                                             │
└─────────────────────────────────────────────────────────────┘
```

### Understanding libuv

**libuv** is the heart of Node.js asynchronous capabilities.

**What libuv Does:**
1. **Event Loop**: Orchestrates all async operations
2. **Thread Pool**: Handles CPU-intensive operations
3. **OS Abstraction**: Cross-platform async I/O
4. **Network I/O**: TCP, UDP, DNS
5. **File I/O**: File system operations
6. **Child Processes**: Spawn and manage processes
7. **Signals**: Handle POSIX signals

**Platform-Specific I/O:**
```
Linux:   epoll
macOS:   kqueue
Windows: IOCP (I/O Completion Ports)
```

### Single-Threaded but Highly Concurrent

```javascript
// This appears to run on one thread
console.log('1. Start');

// These are handled by libuv thread pool
const fs = require('fs');
fs.readFile('file1.txt', () => console.log('2. File 1'));
fs.readFile('file2.txt', () => console.log('3. File 2'));
fs.readFile('file3.txt', () => console.log('4. File 3'));

console.log('5. End');

// Output order:
// 1. Start
// 5. End
// 2. File 1 (or 3 or 4, depends on which finishes first)
// 3. File 2
// 4. File 3
```

**What Actually Happens:**

```
Main Thread (JavaScript):
  ├─ console.log('1. Start')           [executes immediately]
  ├─ fs.readFile('file1.txt', ...)     [delegates to thread pool]
  ├─ fs.readFile('file2.txt', ...)     [delegates to thread pool]
  ├─ fs.readFile('file3.txt', ...)     [delegates to thread pool]
  └─ console.log('5. End')             [executes immediately]

Thread Pool (libuv):
  ├─ Worker 1: Reading file1.txt
  ├─ Worker 2: Reading file2.txt
  └─ Worker 3: Reading file3.txt
        │
        └─► When done, callback added to event loop queue

Event Loop:
  └─ Picks up callbacks and executes them on main thread
```

### Configuring Thread Pool

```javascript
// Default: 4 threads
process.env.UV_THREADPOOL_SIZE = 8;  // Increase to 8

const fs = require('fs');
const crypto = require('crypto');

// These operations will use the thread pool
for (let i = 0; i < 10; i++) {
  crypto.pbkdf2('password', 'salt', 100000, 64, 'sha512', (err, key) => {
    console.log(`${i + 1}. Key generated`);
  });
}

// With 4 threads: First 4 run in parallel, then next 4, then last 2
// With 8 threads: First 8 run in parallel, then last 2
```

### Blocking vs Non-Blocking

```javascript
const fs = require('fs');

// ❌ BLOCKING (Synchronous)
console.log('Reading file...');
const data = fs.readFileSync('large-file.txt');
console.log('File read complete');
console.log('Next task');

// Timeline:
// 0ms:     Reading file...
// 0-1000ms: [BLOCKED - waiting for file]
// 1000ms:   File read complete
// 1000ms:   Next task

// ✅ NON-BLOCKING (Asynchronous)
console.log('Reading file...');
fs.readFile('large-file.txt', (err, data) => {
  console.log('File read complete');
});
console.log('Next task');

// Timeline:
// 0ms:  Reading file...
// 0ms:  Next task (doesn't wait!)
// 500ms: File read complete (when ready)
```

### When to Use Sync vs Async

**Use Synchronous (Blocking):**
```javascript
// ✅ During app initialization (one-time only)
const config = JSON.parse(fs.readFileSync('config.json'));

// ✅ In CLI tools (no concurrent operations)
const userData = fs.readFileSync('user.json');
process.exit(0);
```

**Use Asynchronous (Non-Blocking):**
```javascript
// ✅ In web servers (handle concurrent requests)
app.get('/data', async (req, res) => {
  const data = await fs.promises.readFile('data.json');
  res.json(data);
});

// ✅ For any long-running operations
```

### Performance Implications

```javascript
const http = require('http');
const fs = require('fs');

// ❌ BAD: Blocks entire server for each request
const server = http.createServer((req, res) => {
  const data = fs.readFileSync('data.json');  // BLOCKS!
  res.end(data);
});

// With 100 concurrent requests:
// Request 1: 10ms
// Request 2: 20ms (waits for Request 1)
// Request 3: 30ms (waits for Requests 1 & 2)
// ...
// Request 100: 1000ms!

// ✅ GOOD: Non-blocking, handles concurrently
const server = http.createServer((req, res) => {
  fs.readFile('data.json', (err, data) => {
    if (err) {
      res.writeHead(500);
      return res.end('Error');
    }
    res.end(data);
  });
});

// With 100 concurrent requests:
// All requests start immediately
// All complete in ~10-50ms (depending on file size)
```

---

[Due to length constraints, this is Part 1. The tutorial continues with Parts 2-4 covering modules, async programming, built-in modules, Express.js, databases, testing, and production deployment. Each part maintains the same depth and quality.]

---

**Continue to Part 2** for Modules, npm, Async Programming, Event Loop, and Streams.

**Total Tutorial Length:** ~15,000 lines when complete
**Estimated Reading Time:** 40-50 hours
**Skill Level After Completion:** Production-ready Node.js developer

---

## 📚 Quick Navigation

- [← Back to Top](#-nodejs-complete-mastery-2025---beginner-to-advanced)
- [Part 2: Core Concepts →](#) (Modules, npm, Async, Event Loop)
- [Part 3: Built-in Modules →](#) (fs, http, events, process)
- [Part 4: Advanced Topics →](#) (Express, Databases, Testing, Production)

---

**Made with ❤️ for the Node.js community**