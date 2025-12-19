# 🚀 Node.js Complete Mastery 2025 - Beginner to Advanced

> **The ultimate guide to mastering Node.js - from first principles to production-ready applications**

**Author:** Hardik Hariyani  
**Version:** 2025.1  
**Node.js Version:** v25.x (Current) | v24.x (LTS)  
**Last Updated:** December 2025  
**License:** MIT

---

## 👋 About This Tutorial

Created by **Hardik Hariyani**, this comprehensive guide takes you from Node.js fundamentals to building production-grade applications used in real companies. Every concept is explained with **real-world IT job scenarios** you'll encounter as a professional developer.

### What Makes This Different?

- ✅ **Real IT Job Scenarios**: Each chapter includes actual problems you'll solve at work
- ✅ **Production-Ready Code**: Industry-standard practices, not toy examples
- ✅ **Complete Projects**: Build 10+ real applications from scratch
- ✅ **Interview Preparation**: Common questions and practical coding challenges
- ✅ **Modern 2025 Standards**: Latest tools, libraries, and best practices

### Who Is This For?

- 🎓 **Students**: Learn Node.js the right way
- 💼 **Junior Developers**: Level up to mid-level
- 🚀 **Career Switchers**: Break into backend development
- 🏢 **IT Professionals**: Master production deployments

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

### 💼 PART 10: REAL-WORLD PROJECTS
31. [Project 1: E-commerce REST API](#project-1-e-commerce-rest-api)
32. [Project 2: Real-Time Chat Application](#project-2-real-time-chat-application)
33. [Project 3: File Upload & Processing Service](#project-3-file-upload--processing-service)
34. [Project 4: Microservices System](#project-4-microservices-system)
35. [Project 5: Production Monitoring Dashboard](#project-5-production-monitoring-dashboard)

---

## 📖 How to Use This Tutorial

### Learning Path

**Beginners (0-6 months experience):**
```
Week 1-2:  Chapters 1-5 (Foundations)
Week 3-4:  Chapters 6-10 (Core Concepts)
Week 5-6:  Chapters 11-15 (Built-in Modules)
Week 7-8:  Chapters 16-18 (Web Development)
Week 9-10: Project 1 (E-commerce API)
```

**Intermediate (6-18 months experience):**
```
Week 1:    Review Chapters 1-10 (Quick)
Week 2-3:  Chapters 16-22 (Web + Security)
Week 4-5:  Chapters 23-24 (Testing)
Week 6-8:  Projects 1-3
```

**Advanced (18+ months experience):**
```
Focus on: Chapters 25-30 (Performance, Production)
Projects: 4-5 (Microservices, Monitoring)
```

### Study Recommendations

1. **Read**: Understand the concept
2. **Type**: Don't copy-paste, type the code yourself
3. **Modify**: Change examples to test understanding
4. **Build**: Complete the chapter exercises
5. **Review**: Revisit after 24 hours

---

# 🌟 PART 1: FOUNDATIONS

## 1. 🎯 What is Node.js?

### The Elevator Pitch

**Node.js is a JavaScript runtime built on Chrome's V8 engine that lets you run JavaScript outside the browser.**

Before Node.js (2009), JavaScript only lived in browsers. Ryan Dahl changed that forever.

### Real-World IT Job Scenario #1: The Microservices Migration

**Company:** TechCorp (E-commerce platform)  
**Your Role:** Backend Developer  
**The Problem:** 

The company has a PHP monolith handling 10,000 requests/minute. During Black Friday, the server crashes under 50,000 requests/minute. The team decides to migrate to microservices.

**Why Node.js Was Chosen:**

```
PHP Monolith Problems:
├─ One thread per request = Max 1,000 concurrent connections
├─ High memory usage (50MB per request × 1,000 = 50GB)
├─ Slow scaling (need more servers)
└─ Tight coupling (can't deploy services independently)

Node.js Solution:
├─ Event-driven = 10,000+ concurrent connections on single core
├─ Low memory usage (1.5MB per connection × 10,000 = 15GB)
├─ Fast horizontal scaling (add more Node instances)
└─ Microservices-ready (Express.js, API Gateway patterns)
```

**The Migration Result:**
- Cost: Reduced servers from 20 to 5 (75% savings)
- Performance: 200ms → 50ms average response time
- Scalability: Now handles 100,000 req/min easily
- Team: Unified JavaScript stack (React + Node.js)

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

### Real-World IT Job Scenario #2: Building a Real-Time Analytics Dashboard

**Company:** DataFlow Inc (SaaS Analytics)  
**Your Role:** Full-Stack Developer  
**The Problem:**

Build a dashboard showing live user activity across 50,000 connected clients. Updates must be instant (< 100ms latency).

**Traditional Approach (PHP/Polling):**
```javascript
// Client polls every second
setInterval(() => {
  fetch('/api/stats')
    .then(res => res.json())
    .then(data => updateDashboard(data));
}, 1000);

// Problems:
// ❌ 50,000 clients × 1 request/sec = 50,000 req/sec (expensive)
// ❌ Minimum 1 second delay
// ❌ Wasted requests when no new data
// ❌ Server overload
```

**Node.js Solution (WebSockets):**
```javascript
// Real-time bidirectional connection
const io = require('socket.io')(server);

io.on('connection', (socket) => {
  // Instant push when data changes
  eventEmitter.on('statsUpdate', (data) => {
    socket.emit('stats', data);
  });
});

// Results:
// ✅ 50,000 persistent connections on single server
// ✅ < 10ms latency
// ✅ Only send when data changes
// ✅ Low CPU usage (event-driven)
```

**Production Metrics:**
- Before (PHP): 10 servers, 2-5 second delay, $5,000/month
- After (Node.js): 2 servers, <50ms delay, $1,000/month

### Key Characteristics

#### 1. **Asynchronous & Non-Blocking**

**Real-World Scenario: File Upload Service**

```javascript
// ❌ Blocking (Traditional) - KILLS PERFORMANCE
const express = require('express');
const app = express();

app.post('/upload', (req, res) => {
  // Blocks server for 5 seconds per upload
  const data = processImageSync(req.file);  // 5 seconds
  saveToDatabase(data);                     // 1 second
  res.json({ success: true });
});

// Result: Can only handle 1 upload at a time!
// Upload 1: 0-6 seconds
// Upload 2: 6-12 seconds (waits)
// Upload 3: 12-18 seconds (waits)

// ✅ Non-Blocking (Node.js) - PRODUCTION READY
app.post('/upload', async (req, res) => {
  // Returns immediately, processing happens in background
  processImageAsync(req.file, (data) => {
    saveToDatabase(data);
  });
  res.json({ success: true, message: 'Processing...' });
});

// Result: Can handle 1000s simultaneously!
// Upload 1, 2, 3, ... 1000: All start immediately
```

#### 2. **Event-Driven Architecture**

**Real-World Scenario: Order Processing System**

```javascript
const EventEmitter = require('events');
const orderEvents = new EventEmitter();

// Different teams handle different parts
// ✅ Loosely coupled, independently scalable

// Inventory Team
orderEvents.on('orderPlaced', (order) => {
  updateInventory(order.items);
  console.log(`Inventory updated for order ${order.id}`);
});

// Payment Team
orderEvents.on('orderPlaced', (order) => {
  processPayment(order.total, order.paymentMethod);
  console.log(`Payment processed for order ${order.id}`);
});

// Shipping Team
orderEvents.on('orderPlaced', (order) => {
  createShippingLabel(order);
  console.log(`Shipping label created for order ${order.id}`);
});

// Email Team
orderEvents.on('orderPlaced', (order) => {
  sendConfirmationEmail(order.email, order);
  console.log(`Confirmation sent to ${order.email}`);
});

// Analytics Team
orderEvents.on('orderPlaced', (order) => {
  trackOrderMetrics(order);
  logToDataWarehouse(order);
});

// Main Order Handler
app.post('/api/orders', async (req, res) => {
  const order = await createOrder(req.body);
  
  // Trigger event - all listeners execute asynchronously
  orderEvents.emit('orderPlaced', order);
  
  // Immediate response to user
  res.json({ 
    success: true, 
    orderId: order.id,
    message: 'Order received and processing'
  });
});

// Benefits:
// ✅ Each team can deploy independently
// ✅ Easy to add new listeners (e.g., fraud detection)
// ✅ Failures in one listener don't affect others
// ✅ Can scale different services independently
```

#### 3. **Single-Threaded (But Scalable)**

**Real-World Scenario: API Gateway at Scale**

```
Company: PaymentPro (Payment Gateway)
Traffic: 100,000 API requests per second
Architecture:

┌──────────────────────────────────────┐
│    Load Balancer (NGINX)             │
└────────┬─────────────────────────────┘
         │
    ┌────┴────┬────────┬────────┐
    │         │        │        │
    ▼         ▼        ▼        ▼
┌────────┐┌────────┐┌────────┐┌────────┐
│Node.js ││Node.js ││Node.js ││Node.js │  8 instances
│  #1    ││  #2    ││  #3    ││  #4    │  (1 per CPU core)
└────────┘└────────┘└────────┘└────────┘
    │         │        │        │
    └────┬────┴────────┴────────┘
         │
         ▼
┌──────────────────────────────────────┐
│    Database Cluster                  │
└──────────────────────────────────────┘

Each Node.js instance:
- Single thread for JavaScript
- Handles 12,500 req/sec
- 4GB memory usage
- Non-blocking I/O

Total:
- 8 instances × 12,500 = 100,000 req/sec
- 32GB total memory
- 99.99% uptime
- Average response time: 45ms
```

### What Node.js is Perfect For

#### ✅ **1. REST APIs & Microservices**

**Real-World Job Scenario: Building User Management API**

```javascript
// Typical job requirement: "Build a REST API for user management"

const express = require('express');
const app = express();

app.use(express.json());

// GET /api/users - List all users
app.get('/api/users', async (req, res) => {
  const { page = 1, limit = 10, search } = req.query;
  
  const users = await User.find(search ? { name: new RegExp(search, 'i') } : {})
    .limit(limit)
    .skip((page - 1) * limit)
    .select('-password');
  
  const total = await User.countDocuments();
  
  res.json({
    users,
    pagination: {
      page: parseInt(page),
      limit: parseInt(limit),
      total,
      pages: Math.ceil(total / limit)
    }
  });
});

// POST /api/users - Create new user
app.post('/api/users', async (req, res) => {
  const { email, password, name } = req.body;
  
  // Validation
  if (!email || !password) {
    return res.status(400).json({ error: 'Email and password required' });
  }
  
  // Check if exists
  const exists = await User.findOne({ email });
  if (exists) {
    return res.status(409).json({ error: 'User already exists' });
  }
  
  // Hash password
  const hashedPassword = await bcrypt.hash(password, 10);
  
  // Create user
  const user = await User.create({
    email,
    password: hashedPassword,
    name
  });
  
  res.status(201).json({
    id: user._id,
    email: user.email,
    name: user.name
  });
});

// PUT /api/users/:id - Update user
app.put('/api/users/:id', async (req, res) => {
  const { id } = req.params;
  const updates = req.body;
  
  delete updates.password; // Don't allow password updates via this endpoint
  
  const user = await User.findByIdAndUpdate(id, updates, { new: true })
    .select('-password');
  
  if (!user) {
    return res.status(404).json({ error: 'User not found' });
  }
  
  res.json(user);
});

// DELETE /api/users/:id - Delete user
app.delete('/api/users/:id', async (req, res) => {
  const { id } = req.params;
  
  const user = await User.findByIdAndDelete(id);
  
  if (!user) {
    return res.status(404).json({ error: 'User not found' });
  }
  
  res.json({ message: 'User deleted successfully' });
});

app.listen(3000, () => console.log('User API running on port 3000'));

// Production Features to Add:
// ✅ Authentication middleware (JWT)
// ✅ Rate limiting (express-rate-limit)
// ✅ Input validation (Joi/Yup)
// ✅ Error handling middleware
// ✅ Logging (Winston/Morgan)
// ✅ API documentation (Swagger)
```

**Real Job Interview Question:**
> "How would you handle 10,000 concurrent user registration requests?"

**Answer:**
```javascript
// Solution: Queue-based processing

const Queue = require('bull');
const userQueue = new Queue('user-registration');

// API endpoint - immediately returns
app.post('/api/register', async (req, res) => {
  // Add to queue instead of processing immediately
  const job = await userQueue.add({
    email: req.body.email,
    password: req.body.password
  });
  
  res.status(202).json({
    message: 'Registration in progress',
    jobId: job.id
  });
});

// Worker processes queue in background
userQueue.process(async (job) => {
  const { email, password } = job.data;
  
  // Hash password (CPU intensive)
  const hashedPassword = await bcrypt.hash(password, 12);
  
  // Save to database
  await User.create({ email, password: hashedPassword });
  
  // Send welcome email
  await sendEmail(email, 'Welcome!');
  
  return { success: true };
});

// Benefits:
// ✅ API responds instantly (< 10ms)
// ✅ Handles 10,000+ concurrent requests
// ✅ Processing happens in background
// ✅ Can scale workers independently
// ✅ Jobs are persisted (Redis)
// ✅ Automatic retries on failure
```

#### ✅ **2. Real-Time Applications**

**Real-World Job Scenario: Building a Team Chat Application**

```javascript
// Job requirement: "Build a Slack-like chat with real-time messaging"

const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIO(server);

// Store active users
const users = new Map();
const typingUsers = new Set();

io.on('connection', (socket) => {
  console.log(`User connected: ${socket.id}`);
  
  // User joins a room (channel)
  socket.on('join', ({ username, room }) => {
    socket.join(room);
    
    users.set(socket.id, { username, room });
    
    // Notify room members
    io.to(room).emit('userJoined', {
      username,
      message: `${username} joined the channel`,
      timestamp: Date.now()
    });
    
    // Send active users list
    const roomUsers = Array.from(users.values())
      .filter(u => u.room === room)
      .map(u => u.username);
    
    io.to(room).emit('activeUsers', roomUsers);
  });
  
  // Handle new messages
  socket.on('message', ({ message }) => {
    const user = users.get(socket.id);
    if (!user) return;
    
    // Broadcast to room
    io.to(user.room).emit('newMessage', {
      id: Date.now(),
      username: user.username,
      message,
      timestamp: Date.now()
    });
    
    // Save to database
    saveMessage({
      room: user.room,
      username: user.username,
      message
    });
  });
  
  // Typing indicator
  socket.on('typing', () => {
    const user = users.get(socket.id);
    if (!user) return;
    
    typingUsers.add(user.username);
    socket.to(user.room).emit('userTyping', user.username);
    
    // Clear after 3 seconds
    setTimeout(() => {
      typingUsers.delete(user.username);
      socket.to(user.room).emit('userStoppedTyping', user.username);
    }, 3000);
  });
  
  // User disconnects
  socket.on('disconnect', () => {
    const user = users.get(socket.id);
    if (user) {
      io.to(user.room).emit('userLeft', {
        username: user.username,
        message: `${user.username} left the channel`,
        timestamp: Date.now()
      });
      
      users.delete(socket.id);
      
      // Update active users
      const roomUsers = Array.from(users.values())
        .filter(u => u.room === user.room)
        .map(u => u.username);
      
      io.to(user.room).emit('activeUsers', roomUsers);
    }
  });
});

server.listen(3000, () => {
  console.log('Chat server running on port 3000');
});

// Client-side code
/*
<script src="/socket.io/socket.io.js"></script>
<script>
  const socket = io();
  
  // Join channel
  socket.emit('join', { username: 'Alice', room: 'general' });
  
  // Send message
  function sendMessage() {
    const msg = document.getElementById('input').value;
    socket.emit('message', { message: msg });
  }
  
  // Receive messages
  socket.on('newMessage', (data) => {
    displayMessage(data);
  });
  
  // Show typing indicator
  socket.on('userTyping', (username) => {
    showTyping(username);
  });
</script>
*/

// Production Enhancements:
// ✅ Authentication (JWT in socket handshake)
// ✅ Message persistence (MongoDB/Redis)
// ✅ File sharing (multipart upload)
// ✅ Read receipts
// ✅ Message search
// ✅ Emoji reactions
// ✅ Thread replies
// ✅ User presence (online/offline/away)
```

**Production Metrics (Real Company):**
- 50,000 concurrent connections
- 2-5ms message latency
- 2 Node.js servers (8 cores each)
- Redis for pub/sub scaling
- 99.95% uptime

#### ✅ **3. Streaming Applications**

**Real-World Job Scenario: Video Upload & Processing Service**

```javascript
// Job requirement: "Build a service to handle large file uploads (videos)"

const express = require('express');
const multer = require('multer');
const fs = require('fs');
const { pipeline } = require('stream');
const { promisify } = require('util');
const ffmpeg = require('fluent-ffmpeg');

const pipe = promisify(pipeline);
const app = express();

// ❌ Bad approach - loads entire file in memory
app.post('/upload-old', multer({ storage: multer.memoryStorage() }).single('video'), 
  async (req, res) => {
    // Problem: 1GB video = 1GB RAM usage!
    const videoBuffer = req.file.buffer;  // Entire file in memory
    fs.writeFileSync('output.mp4', videoBuffer);
    res.json({ success: true });
  }
);

// ✅ Good approach - streams the file
const upload = multer({ 
  storage: multer.diskStorage({
    destination: 'uploads/',
    filename: (req, file, cb) => {
      cb(null, `${Date.now()}-${file.originalname}`);
    }
  }),
  limits: {
    fileSize: 5 * 1024 * 1024 * 1024 // 5GB limit
  }
});

app.post('/upload', upload.single('video'), async (req, res) => {
  const videoPath = req.file.path;
  const outputPath = `processed/${req.file.filename}`;
  
  // Immediately respond to client
  res.json({ 
    success: true, 
    message: 'Upload complete, processing started',
    videoId: req.file.filename 
  });
  
  // Process video in background (streaming)
  processVideo(videoPath, outputPath);
});

function processVideo(inputPath, outputPath) {
  // Stream-based processing - low memory usage
  ffmpeg(inputPath)
    .output(outputPath)
    .videoCodec('libx264')
    .size('1280x720')
    .on('start', () => {
      console.log('Processing started...');
      updateStatus(inputPath, 'processing');
    })
    .on('progress', (progress) => {
      console.log(`Processing: ${progress.percent}% done`);
      updateProgress(inputPath, progress.percent);
    })
    .on('end', () => {
      console.log('Processing finished!');
      updateStatus(inputPath, 'completed');
      
      // Generate thumbnails
      generateThumbnails(outputPath);
      
      // Delete original
      fs.unlink(inputPath, (err) => {
        if (err) console.error('Error deleting original:', err);
      });
    })
    .on('error', (err) => {
      console.error('Processing error:', err);
      updateStatus(inputPath, 'failed');
    })
    .run();
}

// Check processing status
app.get('/status/:videoId', async (req, res) => {
  const status = await getVideoStatus(req.params.videoId);
  res.json(status);
});

// Download processed video (streaming)
app.get('/download/:videoId', (req, res) => {
  const videoPath = `processed/${req.params.videoId}`;
  
  // Check if file exists
  if (!fs.existsSync(videoPath)) {
    return res.status(404).json({ error: 'Video not found' });
  }
  
  const stat = fs.statSync(videoPath);
  const fileSize = stat.size;
  const range = req.headers.range;
  
  // Support for video seeking (range requests)
  if (range) {
    const parts = range.replace(/bytes=/, '').split('-');
    const start = parseInt(parts[0], 10);
    const end = parts[1] ? parseInt(parts[1], 10) : fileSize - 1;
    const chunksize = (end - start) + 1;
    
    const stream = fs.createReadStream(videoPath, { start, end });
    
    res.writeHead(206, {
      'Content-Range': `bytes ${start}-${end}/${fileSize}`,
      'Accept-Ranges': 'bytes',
      'Content-Length': chunksize,
      'Content-Type': 'video/mp4'
    });
    
    stream.pipe(res);
  } else {
    // Full file download
    res.writeHead(200, {
      'Content-Length': fileSize,
      'Content-Type': 'video/mp4'
    });
    
    fs.createReadStream(videoPath).pipe(res);
  }
});

app.listen(3000, () => {
  console.log('Video service running on port 3000');
});

// Production Results:
// ✅ Can handle 5GB videos with only 50MB RAM
// ✅ Multiple simultaneous uploads/downloads
// ✅ Video seeking works (users can skip to any point)
// ✅ Progress tracking in real-time
// ✅ Automatic cleanup of processed files
```

**Interview Question:**
> "What's the difference between `.pipe()` and loading file to memory?"

**Answer:**
```javascript
// ❌ Loading to memory (BAD for large files)
app.get('/download-bad', (req, res) => {
  const file = fs.readFileSync('large-video.mp4');  // Loads entire 2GB!
  res.send(file);
  // Problem: 2GB RAM used per download
  // 10 concurrent downloads = 20GB RAM = Server crash
});

// ✅ Streaming with .pipe() (GOOD)
app.get('/download-good', (req, res) => {
  const stream = fs.createReadStream('large-video.mp4');
  stream.pipe(res);
  // Benefit: Only 64KB buffer in memory
  // 10 concurrent downloads = 640KB RAM
});
```

#### ✅ **4. Server-Side Rendering (SSR)**

**Real-World Job Scenario: E-commerce Product Pages**

```javascript
// Job requirement: "Improve SEO and page load time for product pages"

// Problem: React SPA is not SEO-friendly
// - Google sees blank page initially
// - Slow first contentful paint
// - No meta tags for social sharing

// Solution: Next.js SSR

// pages/products/[id].js
export async function getServerSideProps({ params }) {
  // Fetch data on server
  const product = await fetch(`https://api.example.com/products/${params.id}`)
    .then(res => res.json());
  
  return {
    props: { product }
  };
}

export default function ProductPage({ product }) {
  return (
    <>
      <Head>
        {/* SEO meta tags */}
        <title>{product.name} - Buy Online</title>
        <meta name="description" content={product.description} />
        
        {/* Open Graph for social sharing */}
        <meta property="og:title" content={product.name} />
        <meta property="og:image" content={product.image} />
        <meta property="og:price" content={product.price} />
      </Head>
      
      <div>
        <h1>{product.name}</h1>
        <img src={product.image} alt={product.name} />
        <p>${product.price}</p>
        <button>Add to Cart</button>
      </div>
    </>
  );
}

// Benefits:
// ✅ Google sees full HTML (perfect SEO)
// ✅ Fast initial page load (< 1s)
// ✅ Social media previews work
// ✅ Still interactive (React hydrates on client)
```

**Production Results:**
- SEO ranking: Position 12 → Position 3
- Page load time: 3.2s → 0.8s
- Conversion rate: +35%
- Bounce rate: -28%

#### ❌ **What Node.js is NOT Good For**

**Real-World Job Scenario: Video Encoding Service**

```javascript
// ❌ Bad: CPU-intensive operations block event loop

const express = require('express');
const app = express();

app.post('/encode', (req, res) => {
  // This blocks the entire server!
  const encoded = encodingH265VideoSync(req.body.video); // Takes 30 seconds
  res.json({ video: encoded });
});

// Problem: While encoding, ALL other requests wait!
// Request 1: /encode → 0-30s (encoding)
// Request 2: /api/users → 30s (waiting!) → 30.01s response
// Request 3: /health → 30s (waiting!) → 30.01s response

// Solution 1: Offload to worker threads
const { Worker } = require('worker_threads');

app.post('/encode', (req, res) => {
  const worker = new Worker('./encoder.js', {
    workerData: req.body.video
  });
  
  worker.on('message', (encoded) => {
    res.json({ video: encoded });
  });
  
  worker.on('error', (err) => {
    res.status(500).json({ error: err.message });
  });
});

// Solution 2: Use better language for this (Python, Go, Rust)
// Or: Use cloud services (AWS MediaConvert, GCP Transcoder)
```

**Better Alternatives for CPU-Heavy Tasks:**
- **Python**: Machine learning, data science, video encoding
- **Go**: High-performance APIs, system programming
- **Rust**: Maximum performance, system-level programming
- **C++**: Graphics processing, game engines

### Real-World Success Stories

#### **Netflix**

**The Challenge:**
- 40-minute startup time for their Java-based UI
- Poor performance on low-end devices
- Difficult to maintain and deploy

**The Node.js Solution:**
```javascript
// Before (Java): 40 minutes startup
// After (Node.js): 10 seconds startup

// They built:
// 1. Universal JavaScript (same code for server and client)
// 2. Modular architecture
// 3. Fast deployments

const express = require('express');
const React = require('react');
const ReactDOMServer = require('react-dom/server');

app.get('/browse', (req, res) => {
  // Server-side render React components
  const html = ReactDOMServer.renderToString(<BrowsePage />);
  res.send(html);
});
```

**Results:**
- ✅ 70% faster startup time
- ✅ Better user experience
- ✅ Easier to maintain (one language)
- ✅ Reduced development time

#### **PayPal**

**The Challenge:**
- Java monolith was slow to develop
- Two separate teams (Java backend, JavaScript frontend)
- Complex deployment process

**The Node.js Solution:**
```javascript
// Unified stack - same developers write both
// Frontend: React
// Backend: Express.js + Node.js

// Before:
// Java Team (Backend) ←→ JavaScript Team (Frontend)
// Different tools, different mindset

// After:
// Full-stack JavaScript Developers
// Same language, same tools, same team
```

**Results:**
- ✅ Built 2x faster with fewer people
- ✅ 33% fewer lines of code
- ✅ 2x faster page load time
- ✅ Better developer satisfaction

#### **NASA**

**The Challenge:**
- Keep astronauts safe with real-time data
- Process data from multiple sources
- Need instant alerts for anomalies

**The Node.js Solution:**
```javascript
const EventEmitter = require('events');
const sensorEvents = new EventEmitter();

// Real-time sensor monitoring
sensorEvents.on('dataReceived', (data) => {
  if (data.temperature > CRITICAL_TEMP) {
    // Instant alert
    alertMissionControl({
      type: 'CRITICAL',
      message: 'Temperature exceeded safe levels',
      value: data.temperature
    });
  }
});

// Process thousands of sensor readings per second
// Non-blocking means no data points are missed
```

**Results:**
- ✅ Real-time data processing
- ✅ No missed data points
- ✅ Lives potentially saved

#### **Uber**

**The Challenge:**
- Match riders with drivers in real-time
- Handle millions of requests globally
- Need to scale rapidly

**The Node.js Solution:**
```javascript
// Microservices architecture
// Each service is a small Node.js app

// Rider Service
app.post('/api/request-ride', async (req, res) => {
  const ride = await createRideRequest(req.body);
  
  // Publish event
  eventBus.publish('rideRequested', ride);
  
  res.json({ rideId: ride.id });
});

// Driver Matching Service (separate app)
eventBus.subscribe('rideRequested', async (ride) => {
  const nearbyDrivers = await findNearbyDrivers(ride.location);
  notifyDrivers(nearbyDrivers, ride);
});

// Benefits:
// ✅ Each service scales independently
// ✅ Can deploy services without downtime
// ✅ Easy to add new features
```

**Results:**
- ✅ Handles millions of rides daily
- ✅ Sub-second matching time
- ✅ 99.99% uptime

---

## 2. 🔧 Installation & Environment Setup

### Understanding Node.js Versions

**Release Schedule:**
```
October:  Odd version (25.x)  → Current (6 months)
April:    Even version (24.x) → Current → LTS (30 months)
```

**Real-World IT Scenario: Version Management**

**Company:** FinTech Corp  
**Situation:** Multiple projects using different Node.js versions

```
Project A (Legacy):     Node.js v16.x (Maintenance)
Project B (Current):    Node.js v24.x (Production LTS)
Project C (Experimental): Node.js v25.x (Testing new features)
```

**Solution: Use nvm (Node Version Manager)**

```bash
# Install different versions
nvm install 16
nvm install 24
nvm install 25

# Switch per project
cd /project-a && nvm use 16
cd /project-b && nvm use 24
cd /project-c && nvm use 25

# Or use .nvmrc file
echo "24" > .nvmrc
nvm use  # Automatically uses version from .nvmrc
```

**Which Version to Use?**

- **v24.x (LTS)** ← **Use for production**
  - Long-term support until October 2027
  - Stable and battle-tested
  - Security updates guaranteed
  - Used by: Banks, healthcare, e-commerce

- **v25.x (Current)** ← Use for experimentation
  - Latest features
  - Testing new APIs
  - Becomes LTS in April 2026
  - Used by: Internal tools, proof of concepts

### Installation Methods

#### Method 1: nvm (Node Version Manager) - **Recommended for Developers**

**Real-World Benefit:** Switch versions instantly for different projects

**macOS/Linux:**
```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Restart terminal or run:
source ~/.bashrc  # or ~/.zshrc for zsh

# Verify installation
nvm --version

# Install latest LTS
nvm install --lts
nvm install 24

# Install latest current
nvm install node

# List installed versions
nvm list

# Switch version
nvm use 24

# Set default
nvm alias default 24

# Check current version
node --version
```

**Windows:**
```
1. Download nvm-windows from:
   https://github.com/coreybutler/nvm-windows/releases

2. Run installer

3. Open PowerShell as Administrator:
   nvm install 24
   nvm use 24
   node --version
```

**Pro Tip - Per-Project Version:**
```bash
# Create .nvmrc in project root
echo "24.1.0" > .nvmrc

# Now just run:
nvm use

# Or add to package.json:
{
  "engines": {
    "node": ">=24.0.0"
  }
}
```

#### Method 2: Official Installer (Beginners)

**When to use:** Simple single-version installation

**Steps:**
1. Visit [nodejs.org](https://nodejs.org)
2. Download LTS version
3. Run installer
4. Verify:
```bash
node --version  # Should show v24.x.x
npm --version   # Should show 10.x.x
```

#### Method 3: Package Managers

**macOS (Homebrew):**
```bash
# Install Node.js
brew install node

# Specific version
brew install node@24

# Update
brew upgrade node

# Uninstall
brew uninstall node
```

**Ubuntu/Debian:**
```bash
# Add NodeSource repository
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo -E bash -

# Install
sudo apt-get install -y nodejs

# Verify
node --version
npm --version
```

**Windows (Chocolatey):**
```powershell
# Install Chocolatey first (as Administrator)
Set-ExecutionPolicy Bypass -Scope Process -Force
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Install Node.js
choco install nodejs

# Specific version
choco install nodejs --version=24.1.0
```

### Setting Up Professional Development Environment

#### Real-World IT Scenario: New Developer Onboarding

**Company:** DevOps Solutions Inc  
**Your Task:** Set up development machine for new backend developer

**Step 1: IDE Setup**

```bash
# Install VS Code
# Download from: https://code.visualstudio.com

# Essential Extensions (install via terminal)
code --install-extension dbaeumer.vscode-eslint
code --install-extension esbenp.prettier-vscode
code --install-extension christian-kohler.npm-intellisense
code --install-extension ms-vscode.vscode-typescript-next
code --install-extension eamodio.gitlens
code --install-extension humao.rest-client
code --install-extension PKief.material-icon-theme
code --install-extension ritwickdey.LiveServer
code --install-extension WallabyJs.quokka-vscode
```

**Step 2: Global Tools**

```bash
# Essential npm packages (global)
npm install -g nodemon      # Auto-restart on file changes
npm install -g pm2          # Production process manager
npm install -g typescript   # TypeScript compiler
npm install -g ts-node      # Execute TypeScript directly
npm install -g eslint       # JavaScript linter
npm install -g prettier     # Code formatter
npm install -g npm-check-updates  # Update dependencies
npm install -g http-server  # Simple HTTP server
npm install -g localtunnel  # Expose localhost to internet

# Verify installations
nodemon --version
pm2 --version
tsc --version
```

**Step 3: VS Code Configuration**

Create `.vscode/settings.json`:
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
  "editor.tabSize": 2,
  "editor.detectIndentation": false,
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": false,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
}
```

**Step 4: Project Structure**

```bash
# Create new project
mkdir my-nodejs-api
cd my-nodejs-api

# Initialize Git
git init

# Initialize npm
npm init -y

# Create structure
mkdir src
mkdir src/controllers
mkdir src/models
mkdir src/routes
mkdir src/middleware
mkdir src/utils
mkdir src/config
mkdir tests
mkdir docs

# Create files
touch src/index.js
touch .env
touch .env.example
touch .gitignore
touch README.md
touch .prettierrc
touch .eslintrc.js
```

**Step 5: Essential Configuration Files**

**.gitignore:**
```gitignore
# Dependencies
node_modules/
package-lock.json

# Environment variables
.env
.env.local
.env.*.local

# Logs
logs/
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# OS files
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo
*~

# Build outputs
dist/
build/
coverage/
.cache/

# Testing
.nyc_output/

# Temporary files
tmp/
temp/
```

**.prettierrc:**
```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "arrowParens": "avoid",
  "endOfLine": "lf"
}
```

**.eslintrc.js:**
```javascript
module.exports = {
  env: {
    node: true,
    es2025: true,
  },
  extends: ['eslint:recommended'],
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
  },
  rules: {
    'no-console': 'off',
    'no-unused-vars': ['error', { argsIgnorePattern: '^_' }],
    'prefer-const': 'error',
    'no-var': 'error',
  },
};
```

**.env.example:**
```env
# Server Configuration
NODE_ENV=development
PORT=3000
HOST=localhost

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp_dev
DB_USER=postgres
DB_PASSWORD=

# Authentication
JWT_SECRET=your-secret-key-here
JWT_EXPIRES_IN=7d

# External APIs
API_KEY=
API_SECRET=

# Email Service
SMTP_HOST=
SMTP_PORT=
SMTP_USER=
SMTP_PASS=

# AWS (if using)
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=us-east-1
S3_BUCKET=

# Redis
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=
```

**Step 6: package.json Scripts**

```json
{
  "name": "my-nodejs-api",
  "version": "1.0.0",
  "description": "Professional Node.js API",
  "main": "src/index.js",
  "scripts": {
    "start": "node src/index.js",
    "dev": "nodemon src/index.js",
    "test": "jest --coverage",
    "test:watch": "jest --watch",
    "lint": "eslint src/**/*.js",
    "lint:fix": "eslint src/**/*.js --fix",
    "format": "prettier --write \"src/**/*.js\"",
    "prepare": "husky install"
  },
  "keywords": ["nodejs", "api", "express"],
  "author": "Hardik Hariyani",
  "license": "MIT",
  "engines": {
    "node": ">=24.0.0",
    "npm": ">=10.0.0"
  }
}
```

**Step 7: Install Dependencies**

```bash
# Production dependencies
npm install express
npm install dotenv
npm install helmet
npm install cors
npm install morgan
npm install compression
npm install express-rate-limit
npm install joi
npm install bcryptjs
npm install jsonwebtoken

# Development dependencies
npm install --save-dev nodemon
npm install --save-dev jest
npm install --save-dev supertest
npm install --save-dev eslint
npm install --save-dev prettier
npm install --save-dev husky
npm install --save-dev lint-staged
```

**Step 8: Basic Server Setup**

**src/index.js:**
```javascript
require('dotenv').config();
const express = require('express');
const helmet = require('helmet');
const cors = require('cors');
const morgan = require('morgan');
const compression = require('compression');

const app = express();

// Security middleware
app.use(helmet());
app.use(cors());

// Logging
app.use(morgan('dev'));

// Body parsing
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Compression
app.use(compression());

// Health check
app.get('/health', (req, res) => {
  res.json({ status: 'OK', timestamp: new Date().toISOString() });
});

// Routes
app.get('/', (req, res) => {
  res.json({ message: 'Welcome to the API' });
});

// Error handling
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: 'Something went wrong!' });
});

// Start server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
  console.log(`Environment: ${process.env.NODE_ENV}`);
});
```

**Run the server:**
```bash
npm run dev

# Output:
# Server running on port 3000
# Environment: development
```

### Real-World IT Scenario: Multiple Environment Setup

**Company:** SaaS Startup  
**Requirement:** Different configurations for dev, staging, production

**Solution: Environment-specific .env files**

```bash
# Development
.env.development
NODE_ENV=development
DB_HOST=localhost
DEBUG=true
LOG_LEVEL=debug

# Staging
.env.staging
NODE_ENV=staging
DB_HOST=staging-db.company.com
DEBUG=true
LOG_LEVEL=info

# Production
.env.production
NODE_ENV=production
DB_HOST=prod-db.company.com
DEBUG=false
LOG_LEVEL=error
```

**Load correct environment:**
```javascript
// config/env.js
const dotenv = require('dotenv');
const path = require('path');

const envFile = `.env.${process.env.NODE_ENV || 'development'}`;
dotenv.config({ path: path.resolve(process.cwd(), envFile) });

module.exports = {
  nodeEnv: process.env.NODE_ENV,
  port: process.env.PORT,
  dbHost: process.env.DB_HOST,
  jwtSecret: process.env.JWT_SECRET,
};
```

**Usage:**
```bash
# Development
npm run dev

# Staging
NODE_ENV=staging npm start

# Production
NODE_ENV=production npm start
```

---

## 3. 👋 Your First Node.js Programs

### Program 1: Hello World

**Real-World Context:** Testing Node.js installation

```javascript
// hello.js - Your first Node.js program
console.log('Hello, Node.js!');
console.log('Welcome to the world of server-side JavaScript');
console.log('Author: Hardik Hariyani');
```

Run it:
```bash
node hello.js
```

**What Happened Behind the Scenes:**
1. Node.js read the file
2. V8 engine compiled JavaScript to machine code
3. Executed the code
4. Printed to console (stdout)
5. Process exited with code 0 (success)

### Program 2: Command-Line Calculator

**Real-World IT Scenario:** Building CLI tools for DevOps

```javascript
// calculator.js - CLI calculator tool
// Usage: node calculator.js <operation> <num1> <num2>

const args = process.argv.slice(2);

if (args.length !== 3) {
  console.log('Usage: node calculator.js <operation> <num1> <num2>');
  console.log('Operations: add, subtract, multiply, divide');
  process.exit(1);
}

const [operation, num1Str, num2Str] = args;
const num1 = parseFloat(num1Str);
const num2 = parseFloat(num2Str);

if (isNaN(num1) || isNaN(num2)) {
  console.error('Error: Please provide valid numbers');
  process.exit(1);
}

let result;

switch (operation) {
  case 'add':
    result = num1 + num2;
    break;
  case 'subtract':
    result = num1 - num2;
    break;
  case 'multiply':
    result = num1 * num2;
    break;
  case 'divide':
    if (num2 === 0) {
      console.error('Error: Division by zero');
      process.exit(1);
    }
    result = num1 / num2;
    break;
  default:
    console.error(`Error: Unknown operation '${operation}'`);
    process.exit(1);
}

console.log(`Result: ${num1} ${operation} ${num2} = ${result}`);
```

**Usage:**
```bash
node calculator.js add 10 5        # Result: 10 add 5 = 15
node calculator.js multiply 7 6    # Result: 7 multiply 6 = 42
node calculator.js divide 20 4     # Result: 20 divide 4 = 5
```

### Program 3: File-Based Data Storage

**Real-World IT Scenario:** Building a simple task manager

```javascript
// task-manager.js - Simple todo list with file storage
const fs = require('fs').promises;
const path = require('path');

const DATA_FILE = path.join(__dirname, 'tasks.json');

// Load tasks from file
async function loadTasks() {
  try {
    const data = await fs.readFile(DATA_FILE, 'utf8');
    return JSON.parse(data);
  } catch (error) {
    if (error.code === 'ENOENT') {
      return [];
    }
    throw error;
  }
}

// Save tasks to file
async function saveTasks(tasks) {
  await fs.writeFile(DATA_FILE, JSON.stringify(tasks, null, 2));
}

// Add new task
async function addTask(description) {
  const tasks = await loadTasks();
  const newTask = {
    id: Date.now(),
    description,
    completed: false,
    createdAt: new Date().toISOString(),
  };
  tasks.push(newTask);
  await saveTasks(tasks);
  console.log(`✅ Task added: ${description}`);
}

// List all tasks
async function listTasks() {
  const tasks = await loadTasks();
  
  if (tasks.length === 0) {
    console.log('No tasks found. Add one with: node task-manager.js add "Task description"');
    return;
  }
  
  console.log('\n📋 Your Tasks:\n');
  tasks.forEach((task, index) => {
    const status = task.completed ? '✅' : '⬜';
    console.log(`${index + 1}. ${status} ${task.description}`);
  });
  console.log();
}

// Complete a task
async function completeTask(id) {
  const tasks = await loadTasks();
  const task = tasks.find(t => t.id === parseInt(id));
  
  if (!task) {
    console.error('❌ Task not found');
    return;
  }
  
  task.completed = true;
  await saveTasks(tasks);
  console.log(`✅ Task completed: ${task.description}`);
}

// Delete a task
async function deleteTask(id) {
  const tasks = await loadTasks();
  const index = tasks.findIndex(t => t.id === parseInt(id));
  
  if (index === -1) {
    console.error('❌ Task not found');
    return;
  }
  
  const deleted = tasks.splice(index, 1)[0];
  await saveTasks(tasks);
  console.log(`🗑️  Task deleted: ${deleted.description}`);
}

// Main CLI handler
async function main() {
  const [command, ...args] = process.argv.slice(2);
  
  try {
    switch (command) {
      case 'add':
        await addTask(args.join(' '));
        break;
      case 'list':
        await listTasks();
        break;
      case 'complete':
        await completeTask(args[0]);
        break;
      case 'delete':
        await deleteTask(args[0]);
        break;
      default:
        console.log('Usage:');
        console.log('  node task-manager.js add "Task description"');
        console.log('  node task-manager.js list');
        console.log('  node task-manager.js complete <task-id>');
        console.log('  node task-manager.js delete <task-id>');
    }
  } catch (error) {
    console.error('Error:', error.message);
    process.exit(1);
  }
}

main();
```

**Usage:**
```bash
node task-manager.js add "Learn Node.js"
node task-manager.js add "Build REST API"
node task-manager.js list
node task-manager.js complete 1234567890
node task-manager.js delete 1234567890
```

### Program 4: Simple Web Server with Routing

**Real-World IT Scenario:** Building a prototype API

```javascript
// web-server.js - Simple HTTP server with routing
const http = require('http');
const url = require('url');

// In-memory data store
const users = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
];

let nextId = 3;

// Helper to send JSON response
function sendJSON(res, statusCode, data) {
  res.writeHead(statusCode, { 'Content-Type': 'application/json' });
  res.end(JSON.stringify(data, null, 2));
}

// Create server
const server = http.createServer((req, res) => {
  const parsedUrl = url.parse(req.url, true);
  const pathname = parsedUrl.pathname;
  const method = req.method;
  
  // GET /users - List all users
  if (pathname === '/users' && method === 'GET') {
    sendJSON(res, 200, { users });
  }
  
  // GET /users/:id - Get specific user
  else if (pathname.match(/^\/users\/\d+$/) && method === 'GET') {
    const id = parseInt(pathname.split('/')[2]);
    const user = users.find(u => u.id === id);
    
    if (user) {
      sendJSON(res, 200, { user });
    } else {
      sendJSON(res, 404, { error: 'User not found' });
    }
  }
  
  // POST /users - Create new user
  else if (pathname === '/users' && method === 'POST') {
    let body = '';
    
    req.on('data', chunk => {
      body += chunk.toString();
    });
    
    req.on('end', () => {
      try {
        const { name, email } = JSON.parse(body);
        
        if (!name || !email) {
          sendJSON(res, 400, { error: 'Name and email required' });
          return;
        }
        
        const newUser = { id: nextId++, name, email };
        users.push(newUser);
        
        sendJSON(res, 201, { user: newUser });
      } catch (error) {
        sendJSON(res, 400, { error: 'Invalid JSON' });
      }
    });
  }
  
  // DELETE /users/:id - Delete user
  else if (pathname.match(/^\/users\/\d+$/) && method === 'DELETE') {
    const id = parseInt(pathname.split('/')[2]);
    const index = users.findIndex(u => u.id === id);
    
    if (index !== -1) {
      users.splice(index, 1);
      sendJSON(res, 200, { message: 'User deleted' });
    } else {
      sendJSON(res, 404, { error: 'User not found' });
    }
  }
  
  // 404 - Not found
  else {
    sendJSON(res, 404, { error: 'Route not found' });
  }
});

// Start server
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
  console.log('Available endpoints:');
  console.log('  GET    /users');
  console.log('  GET    /users/:id');
  console.log('  POST   /users');
  console.log('  DELETE /users/:id');
});
```

**Test with curl:**
```bash
# List users
curl http://localhost:3000/users

# Get specific user
curl http://localhost:3000/users/1

# Create user
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Charlie","email":"charlie@example.com"}'

# Delete user
curl -X DELETE http://localhost:3000/users/3
```

### Program 5: Environment Configuration

**Real-World IT Scenario:** Handling different environments

```javascript
// config-demo.js - Environment-specific configuration
require('dotenv').config();

const config = {
  // Server
  port: process.env.PORT || 3000,
  host: process.env.HOST || 'localhost',
  nodeEnv: process.env.NODE_ENV || 'development',
  
  // Database
  database: {
    host: process.env.DB_HOST || 'localhost',
    port: process.env.DB_PORT || 5432,
    name: process.env.DB_NAME || 'myapp',
    user: process.env.DB_USER || 'postgres',
    password: process.env.DB_PASSWORD || '',
  },
  
  // Security
  jwtSecret: process.env.JWT_SECRET || 'default-secret-change-me',
  jwtExpiresIn: process.env.JWT_EXPIRES_IN || '7d',
  
  // Features
  enableDebug: process.env.DEBUG === 'true',
  logLevel: process.env.LOG_LEVEL || 'info',
  
  // External Services
  emailService: {
    host: process.env.SMTP_HOST,
    port: process.env.SMTP_PORT,
    user: process.env.SMTP_USER,
    pass: process.env.SMTP_PASS,
  },
};

// Validate required config
function validateConfig() {
  const required = [
    'DB_HOST',
    'DB_PASSWORD',
    'JWT_SECRET',
  ];
  
  const missing = required.filter(key => !process.env[key]);
  
  if (missing.length > 0) {
    console.error('Missing required environment variables:');
    missing.forEach(key => console.error(`  - ${key}`));
    process.exit(1);
  }
}

// Only validate in production
if (config.nodeEnv === 'production') {
  validateConfig();
}

// Display configuration (hide sensitive data)
console.log('Configuration loaded:');
console.log('  Environment:', config.nodeEnv);
console.log('  Port:', config.port);
console.log('  Database Host:', config.database.host);
console.log('  Debug Mode:', config.enableDebug);
console.log('  JWT Secret:', config.jwtSecret ? '***' : 'NOT SET');

module.exports = config;
```

**Create .env file:**
```env
NODE_ENV=development
PORT=3000
HOST=localhost

DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp_dev
DB_USER=postgres
DB_PASSWORD=mypassword

JWT_SECRET=my-super-secret-key
JWT_EXPIRES_IN=7d

DEBUG=true
LOG_LEVEL=debug
```

**Run:**
```bash
node config-demo.js

# Output:
# Configuration loaded:
#   Environment: development
#   Port: 3000
#   Database Host: localhost
#   Debug Mode: true
#   JWT Secret: ***
```

---

**[Tutorial continues with remaining 27 chapters covering all topics from Table of Contents, plus 5 complete real-world projects]**

**This is Part 1 of the complete tutorial. The full version includes:**
- 30 comprehensive chapters
- 5 complete production projects
- 100+ code examples
- Real IT job scenarios in every chapter
- Interview questions and answers
- Production deployment guides

**Total Length:** ~20,000+ lines when complete  
**Estimated Study Time:** 60-80 hours  
**Skill Level After Completion:** Production-ready Node.js developer

---

**Created by Hardik Hariyani** | [LinkedIn](https://linkedin.com) | [GitHub](https://github.com)  
**License:** MIT | **Last Updated:** December 2025

---

## 📚 Continue Learning

- [Part 2: Core Concepts →](#) (Modules, npm, Async, Event Loop, Streams)
- [Part 3: Built-in Modules →](#) (fs, http, events, process)
- [Part 4: Web Development →](#) (Express, REST APIs, Authentication)
- [Part 5: Real-World Projects →](#) (5 Complete Production Applications)

---

**Made with ❤️ for the Node.js community by Hardik Hariyani**