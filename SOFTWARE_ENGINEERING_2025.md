# 🚀 Software Engineering 2025 - Complete Tutorial & Cheat Sheet

> **Modern best practices, patterns, and tools for building exceptional software**

---

## 📚 Table of Contents

1. [Core Principles](#-core-principles)
2. [SOLID Principles](#-solid-principles)
3. [Design Patterns](#-design-patterns)
4. [Architecture Patterns](#-architecture-patterns)
5. [Clean Code Practices](#-clean-code-practices)
6. [Version Control & Git](#-version-control--git)
7. [CI/CD & DevOps](#-cicd--devops)
8. [Testing Strategies](#-testing-strategies)
9. [Security Best Practices](#-security-best-practices)
10. [Modern Development Tools](#-modern-development-tools)
11. [AI-Powered Development](#-ai-powered-development)
12. [Quick Reference](#-quick-reference)

---

## 🎯 Core Principles

### The Four Pillars

#### **1. KISS - Keep It Simple, Stupid**
- Choose the simplest solution that works
- Avoid over-engineering
- Complexity is your enemy

**Example:**
```javascript
// ❌ Over-engineered
class DataProcessor {
  constructor(strategy, validator, logger, cache) {
    this.strategy = strategy;
    this.validator = validator;
    // ...10 more dependencies
  }
}

// ✅ Simple
function processData(data) {
  return data.filter(item => item.valid).map(transform);
}
```

#### **2. YAGNI - You Aren't Gonna Need It**
- Don't write code for future "maybe" requirements
- Build what you need now
- Requirements change; unused code is wasted effort

#### **3. DRY - Don't Repeat Yourself**
- Every piece of knowledge should have a single representation
- Reduce duplication through abstraction
- But don't create premature abstractions

#### **4. Separation of Concerns**
- Each module handles one specific aspect
- Changes in one area don't ripple everywhere
- Easier testing and maintenance

---

## 🏛️ SOLID Principles

### **S - Single Responsibility Principle**

A class should have only ONE reason to change.

```python
# ❌ Multiple responsibilities
class User:
    def save_to_database(self):
        # Database logic
        pass
    
    def send_email(self):
        # Email logic
        pass
    
    def generate_report(self):
        # Reporting logic
        pass

# ✅ Single responsibility
class User:
    def __init__(self, name, email):
        self.name = name
        self.email = email

class UserRepository:
    def save(self, user):
        # Database logic
        pass

class EmailService:
    def send(self, user, message):
        # Email logic
        pass

class ReportGenerator:
    def generate(self, user):
        # Reporting logic
        pass
```

**Benefits:**
- Easier to understand
- Simpler to test
- Less likely to break when changes occur

### **O - Open/Closed Principle**

Open for extension, closed for modification.

```typescript
// ❌ Violates OCP - must modify class to add payment methods
class PaymentProcessor {
  processPayment(type: string, amount: number) {
    if (type === 'credit') {
      // credit card logic
    } else if (type === 'paypal') {
      // paypal logic
    }
    // Adding new payment requires modifying this class
  }
}

// ✅ Follows OCP - extend via new classes
interface PaymentMethod {
  process(amount: number): void;
}

class CreditCardPayment implements PaymentMethod {
  process(amount: number) {
    // credit card logic
  }
}

class PayPalPayment implements PaymentMethod {
  process(amount: number) {
    // paypal logic
  }
}

class CryptoPayment implements PaymentMethod {
  process(amount: number) {
    // crypto logic - NEW, no modification needed!
  }
}
```

### **L - Liskov Substitution Principle**

Subtypes must be substitutable for their base types.

```java
// ❌ Violates LSP
class Bird {
    public void fly() {
        // flying logic
    }
}

class Penguin extends Bird {
    @Override
    public void fly() {
        throw new UnsupportedOperationException("Penguins can't fly!");
    }
}

// ✅ Follows LSP
interface Bird {
    void move();
}

class FlyingBird implements Bird {
    public void move() {
        fly();
    }
    
    private void fly() {
        // flying logic
    }
}

class Penguin implements Bird {
    public void move() {
        swim();
    }
    
    private void swim() {
        // swimming logic
    }
}
```

### **I - Interface Segregation Principle**

Clients shouldn't depend on interfaces they don't use.

```csharp
// ❌ Fat interface
interface IWorker
{
    void Work();
    void Eat();
    void Sleep();
}

// ✅ Segregated interfaces
interface IWorkable
{
    void Work();
}

interface IFeedable
{
    void Eat();
}

interface IRestable
{
    void Sleep();
}

class Human : IWorkable, IFeedable, IRestable
{
    public void Work() { }
    public void Eat() { }
    public void Sleep() { }
}

class Robot : IWorkable
{
    public void Work() { }
    // Robots don't eat or sleep
}
```

### **D - Dependency Inversion Principle**

Depend on abstractions, not concretions.

```javascript
// ❌ High-level depends on low-level
class MySQLDatabase {
  save(data) { /* MySQL specific */ }
}

class UserService {
  constructor() {
    this.db = new MySQLDatabase(); // Tightly coupled
  }
}

// ✅ Both depend on abstraction
interface Database {
  save(data: any): void;
}

class MySQLDatabase implements Database {
  save(data) { /* MySQL specific */ }
}

class PostgreSQLDatabase implements Database {
  save(data) { /* PostgreSQL specific */ }
}

class UserService {
  constructor(private db: Database) {
    // Depends on abstraction, can use any database
  }
}
```

---

## 🎨 Design Patterns

### Creational Patterns

#### **1. Singleton**
Ensures only one instance exists.

```python
class Database:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
            # Initialize connection
        return cls._instance

# Always returns the same instance
db1 = Database()
db2 = Database()
# db1 is db2 == True
```

**Use when:** Managing shared resources (database connections, logging, caching)

#### **2. Factory**
Creates objects without specifying exact class.

```java
interface Vehicle {
    void drive();
}

class Car implements Vehicle {
    public void drive() { /* car logic */ }
}

class Truck implements Vehicle {
    public void drive() { /* truck logic */ }
}

class VehicleFactory {
    public static Vehicle createVehicle(String type) {
        return switch(type) {
            case "car" -> new Car();
            case "truck" -> new Truck();
            default -> throw new IllegalArgumentException();
        };
    }
}

// Usage
Vehicle vehicle = VehicleFactory.createVehicle("car");
```

**Use when:** Object creation logic is complex or should be centralized

#### **3. Builder**
Constructs complex objects step by step.

```typescript
class Pizza {
  private size: string;
  private cheese: boolean;
  private pepperoni: boolean;
  private vegetables: string[];

  constructor(builder: PizzaBuilder) {
    this.size = builder.size;
    this.cheese = builder.cheese;
    this.pepperoni = builder.pepperoni;
    this.vegetables = builder.vegetables;
  }
}

class PizzaBuilder {
  size: string = "medium";
  cheese: boolean = true;
  pepperoni: boolean = false;
  vegetables: string[] = [];

  setSize(size: string): this {
    this.size = size;
    return this;
  }

  addCheese(): this {
    this.cheese = true;
    return this;
  }

  addPepperoni(): this {
    this.pepperoni = true;
    return this;
  }

  addVegetables(veggies: string[]): this {
    this.vegetables = veggies;
    return this;
  }

  build(): Pizza {
    return new Pizza(this);
  }
}

// Usage - Clean and readable
const pizza = new PizzaBuilder()
  .setSize("large")
  .addCheese()
  .addPepperoni()
  .addVegetables(["mushrooms", "onions"])
  .build();
```

**Use when:** Objects have many optional parameters or complex construction

### Structural Patterns

#### **1. Adapter**
Makes incompatible interfaces work together.

```javascript
// Old API
class OldPaymentGateway {
  makePayment(amount) {
    return `Old API: Paid ${amount}`;
  }
}

// New interface expected
interface PaymentProcessor {
  processPayment(amount: number): string;
}

// Adapter
class PaymentAdapter implements PaymentProcessor {
  constructor(private oldGateway: OldPaymentGateway) {}
  
  processPayment(amount: number): string {
    return this.oldGateway.makePayment(amount);
  }
}

// Usage - works seamlessly
const adapter = new PaymentAdapter(new OldPaymentGateway());
console.log(adapter.processPayment(100));
```

**Use when:** Integrating legacy code or third-party libraries

#### **2. Decorator**
Adds behavior to objects dynamically.

```python
# Base component
class Coffee:
    def cost(self):
        return 5
    
    def description(self):
        return "Coffee"

# Decorators
class MilkDecorator:
    def __init__(self, coffee):
        self._coffee = coffee
    
    def cost(self):
        return self._coffee.cost() + 1
    
    def description(self):
        return self._coffee.description() + ", Milk"

class SugarDecorator:
    def __init__(self, coffee):
        self._coffee = coffee
    
    def cost(self):
        return self._coffee.cost() + 0.5
    
    def description(self):
        return self._coffee.description() + ", Sugar"

# Usage - flexible combinations
coffee = Coffee()
coffee = MilkDecorator(coffee)
coffee = SugarDecorator(coffee)

print(f"{coffee.description()}: ${coffee.cost()}")
# Output: Coffee, Milk, Sugar: $6.5
```

**Use when:** Need to add responsibilities without subclassing

### Behavioral Patterns

#### **1. Observer**
Notifies dependents when state changes.

```typescript
interface Observer {
  update(data: any): void;
}

class Subject {
  private observers: Observer[] = [];
  
  attach(observer: Observer): void {
    this.observers.push(observer);
  }
  
  detach(observer: Observer): void {
    const index = this.observers.indexOf(observer);
    this.observers.splice(index, 1);
  }
  
  notify(data: any): void {
    this.observers.forEach(observer => observer.update(data));
  }
}

// Real-world example
class WeatherStation extends Subject {
  private temperature: number = 0;
  
  setTemperature(temp: number): void {
    this.temperature = temp;
    this.notify({ temperature: temp });
  }
}

class PhoneDisplay implements Observer {
  update(data: any): void {
    console.log(`Phone: Temperature is ${data.temperature}°C`);
  }
}

class WebDisplay implements Observer {
  update(data: any): void {
    console.log(`Website: It's ${data.temperature}°C outside`);
  }
}

// Usage
const station = new WeatherStation();
station.attach(new PhoneDisplay());
station.attach(new WebDisplay());
station.setTemperature(25); // Both displays update
```

**Use when:** Multiple objects need to react to state changes

#### **2. Strategy**
Selects algorithm at runtime.

```java
interface SortingStrategy {
    void sort(int[] array);
}

class QuickSort implements SortingStrategy {
    public void sort(int[] array) {
        // Quick sort implementation
    }
}

class MergeSort implements SortingStrategy {
    public void sort(int[] array) {
        // Merge sort implementation
    }
}

class Sorter {
    private SortingStrategy strategy;
    
    public void setStrategy(SortingStrategy strategy) {
        this.strategy = strategy;
    }
    
    public void sort(int[] array) {
        strategy.sort(array);
    }
}

// Usage - swap algorithms easily
Sorter sorter = new Sorter();
sorter.setStrategy(new QuickSort());
sorter.sort(smallArray);

sorter.setStrategy(new MergeSort());
sorter.sort(largeArray);
```

**Use when:** Multiple algorithms are interchangeable

---

## 🏗️ Architecture Patterns

### **1. Microservices Architecture**

**Best for:** Large, complex applications requiring scalability and flexibility

**Structure:**
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   User      │     │   Order     │     │   Payment   │
│  Service    │────▶│  Service    │────▶│   Service   │
└─────────────┘     └─────────────┘     └─────────────┘
      │                   │                     │
      ▼                   ▼                     ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  User DB    │     │  Order DB   │     │ Payment DB  │
└─────────────┘     └─────────────┘     └─────────────┘
```

**Characteristics:**
- ✅ Independent deployment
- ✅ Technology diversity
- ✅ Fault isolation
- ✅ Easy scaling
- ❌ Complex infrastructure
- ❌ Distributed system challenges
- ❌ Data consistency issues

**Real-world examples:** Netflix, Amazon, Uber

### **2. Layered (N-Tier) Architecture**

**Best for:** Traditional business applications

**Structure:**
```
┌────────────────────────────────┐
│    Presentation Layer          │  ← UI, API endpoints
├────────────────────────────────┤
│    Business Logic Layer        │  ← Domain logic, rules
├────────────────────────────────┤
│    Data Access Layer           │  ← Database operations
├────────────────────────────────┤
│    Database Layer              │  ← Data storage
└────────────────────────────────┘
```

**Characteristics:**
- ✅ Clear separation
- ✅ Easy to understand
- ✅ Straightforward testing
- ❌ Can become monolithic
- ❌ Tight coupling between layers

**Use when:** Building standard CRUD applications

### **3. Event-Driven Architecture**

**Best for:** Real-time systems, reactive applications

**Structure:**
```
   Event Producer          Event Bus          Event Consumers
┌────────────────┐    ┌──────────────┐    ┌──────────────┐
│  User Action   │───▶│  Event Queue │───▶│   Logger     │
└────────────────┘    └──────────────┘    └──────────────┘
                             │              ┌──────────────┐
                             └─────────────▶│  Notifier    │
                                            └──────────────┘
                                            ┌──────────────┐
                                            │  Analytics   │
                                            └──────────────┘
```

**Characteristics:**
- ✅ Highly decoupled
- ✅ Scalable
- ✅ Asynchronous
- ❌ Complex debugging
- ❌ Event ordering challenges

**Real-world examples:** E-commerce (order processing), IoT systems, financial trading

### **4. Serverless Architecture**

**Best for:** Variable workloads, rapid prototyping

**Structure:**
```
Client ──▶ API Gateway ──▶ Lambda Functions ──▶ Services
                              │
                              ├─▶ Database
                              ├─▶ Storage
                              └─▶ Third-party APIs
```

**Characteristics:**
- ✅ No server management
- ✅ Auto-scaling
- ✅ Pay per use
- ❌ Cold starts
- ❌ Vendor lock-in
- ❌ Limited control

**Use when:** Unpredictable traffic, event-driven workloads

### **5. Hexagonal (Ports and Adapters)**

**Best for:** Domain-focused applications, testing

**Structure:**
```
           ┌──────────────────────┐
           │   External Systems   │
           └─────────┬────────────┘
                     │
           ┌─────────▼────────────┐
           │      Adapters        │  ← Database, API, UI
           ├──────────────────────┤
           │       Ports          │  ← Interfaces
           ├──────────────────────┤
           │   Business Logic     │  ← Core domain
           └──────────────────────┘
```

**Characteristics:**
- ✅ Testable core
- ✅ Framework independent
- ✅ Flexible adapters
- ❌ More initial setup
- ❌ Learning curve

**Use when:** Domain logic is complex and should be isolated

---

## ✨ Clean Code Practices

### Naming Conventions

```javascript
// ❌ Bad names
const d = new Date();
const x = getUserData();
function calc(a, b) { return a + b; }

// ✅ Good names
const currentDate = new Date();
const userData = getUserData();
function calculateTotal(price, tax) { return price + tax; }
```

**Rules:**
- Use descriptive, pronounceable names
- Avoid abbreviations (except common ones like `id`, `url`)
- Class names: Nouns (User, OrderProcessor)
- Function names: Verbs (calculateTotal, sendEmail)
- Boolean variables: is/has/can prefix (isValid, hasPermission)

### Functions

```python
# ❌ Too long, does too much
def process_order(order):
    # Validate order (20 lines)
    # Calculate total (15 lines)
    # Apply discounts (25 lines)
    # Update inventory (30 lines)
    # Send confirmation (10 lines)
    # Log transaction (5 lines)
    pass  # 100+ lines total

# ✅ Small, focused functions
def validate_order(order):
    # 5 lines
    pass

def calculate_order_total(order):
    # 5 lines
    pass

def apply_discounts(total, user):
    # 5 lines
    pass

def update_inventory(order):
    # 5 lines
    pass

def send_order_confirmation(order, user):
    # 5 lines
    pass

def process_order(order, user):
    validate_order(order)
    total = calculate_order_total(order)
    total = apply_discounts(total, user)
    update_inventory(order)
    send_order_confirmation(order, user)
    log_transaction(order)
```

**Rules:**
- Keep functions small (< 20 lines ideal)
- Do one thing
- One level of abstraction
- Maximum 3 parameters (use objects for more)

### Comments

```java
// ❌ Bad comments

// This increments i by 1
i++;

// Written by John on 2024-05-15
public void processData() { }

// Don't change this code!
private void legacyMethod() { }

// ✅ Good comments

/**
 * Calculates compound interest using the formula: A = P(1 + r/n)^(nt)
 * 
 * @param principal Initial investment amount
 * @param rate Annual interest rate (decimal)
 * @param years Time period in years
 * @return Final amount after interest
 */
public double calculateCompoundInterest(double principal, double rate, int years) {
    return principal * Math.pow(1 + rate, years);
}

// HACK: Using setTimeout as temporary fix for race condition
// TODO: Implement proper async handling in ticket #1234
setTimeout(() => processData(), 100);

// WARNING: This API has rate limits of 100 requests/minute
fetchExternalData();
```

**Rules:**
- Code should be self-explanatory
- Comment "why", not "what"
- Use TODOs, FIXMEs, HACKs appropriately
- Keep comments updated with code

### Error Handling

```typescript
// ❌ Silent failures
try {
  processPayment(amount);
} catch (e) {
  // Swallows error
}

// ❌ Generic catching
try {
  complexOperation();
} catch (Exception e) {
  console.log("Error");
}

// ✅ Specific, actionable error handling
class PaymentError extends Error {
  constructor(message: string, public code: string) {
    super(message);
  }
}

async function processPayment(amount: number): Promise<void> {
  if (amount <= 0) {
    throw new PaymentError('Amount must be positive', 'INVALID_AMOUNT');
  }
  
  try {
    await gateway.charge(amount);
  } catch (error) {
    if (error.code === 'INSUFFICIENT_FUNDS') {
      throw new PaymentError('Insufficient funds', 'INSUFFICIENT_FUNDS');
    }
    if (error.code === 'NETWORK_ERROR') {
      // Retry logic
      await retryPayment(amount);
    }
    throw error; // Re-throw unknown errors
  }
}

// Usage with proper handling
try {
  await processPayment(100);
} catch (error) {
  if (error instanceof PaymentError) {
    switch (error.code) {
      case 'INVALID_AMOUNT':
        showMessage('Please enter valid amount');
        break;
      case 'INSUFFICIENT_FUNDS':
        showMessage('Insufficient funds');
        break;
    }
  } else {
    logger.error('Unexpected error', error);
    showMessage('Payment failed. Please try again.');
  }
}
```

---

## 🔄 Version Control & Git

### Essential Git Commands

```bash
# Configuration
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Repository basics
git init                    # Initialize repository
git clone <url>             # Clone repository
git status                  # Check status
git log --oneline --graph   # View history

# Branching
git branch feature-x        # Create branch
git checkout feature-x      # Switch to branch
git checkout -b feature-x   # Create and switch

# Modern alternative
git switch feature-x        # Switch branch
git switch -c feature-x     # Create and switch

# Working with changes
git add <file>              # Stage specific file
git add .                   # Stage all changes
git commit -m "message"     # Commit with message
git commit --amend          # Modify last commit

# Syncing
git fetch origin            # Download changes
git pull origin main        # Fetch and merge
git push origin feature-x   # Push branch

# Merging
git merge feature-x         # Merge branch
git rebase main             # Rebase onto main

# Stashing
git stash                   # Save work temporarily
git stash pop               # Restore stashed work
git stash list              # View stashes
```

### Git Workflow (Feature Branch)

```
main ─────●─────────────●─────────▶
           \           /
            ●─────●───●  feature-x
```

**Process:**
```bash
# 1. Create feature branch
git checkout -b feature/user-authentication

# 2. Make changes and commit
git add src/auth.js
git commit -m "Add user authentication"

# 3. Keep branch updated
git checkout main
git pull origin main
git checkout feature/user-authentication
git rebase main

# 4. Push and create pull request
git push origin feature/user-authentication

# 5. After review and approval, merge via GitHub/GitLab
# Then clean up
git checkout main
git pull origin main
git branch -d feature/user-authentication
```

### Commit Message Best Practices

```
✅ Good commit messages:
feat: Add user authentication with JWT
fix: Resolve memory leak in image processor
docs: Update API documentation for v2.0
refactor: Simplify payment processing logic
test: Add unit tests for UserService
chore: Update dependencies to latest versions

❌ Bad commit messages:
"Fixed stuff"
"WIP"
"asdfasdf"
"Updated files"
```

**Format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance

### .gitignore Essentials

```gitignore
# Dependencies
node_modules/
vendor/
*.pyc
__pycache__/

# Environment
.env
.env.local
.env.production

# IDE
.vscode/
.idea/
*.swp
*.swo

# Build outputs
dist/
build/
*.log
*.out

# OS files
.DS_Store
Thumbs.db

# Sensitive files
*.key
*.pem
secrets.yml
```

---

## 🔄 CI/CD & DevOps

### CI/CD Pipeline Overview

```
┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐
│  Commit  │──▶│  Build   │──▶│   Test   │──▶│  Deploy  │──▶│ Monitor  │
│   Code   │   │  & Lint  │   │   All    │   │  to Prod │   │  System  │
└──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘
     │              │              │              │              │
     │         Compile         Unit Tests    Staging        Metrics
     │         Bundle          Integration   Canary         Logs
     │         Validate        E2E Tests     Blue/Green     Alerts
```

### Popular CI/CD Tools (2025)

#### **1. GitHub Actions** (Most popular for personal projects - 62% usage)
```yaml
# .github/workflows/ci.yml
name: CI Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '20'
    
    - name: Install dependencies
      run: npm ci
    
    - name: Run linter
      run: npm run lint
    
    - name: Run tests
      run: npm test
    
    - name: Build
      run: npm run build
    
    - name: Deploy to staging
      if: github.ref == 'refs/heads/develop'
      run: npm run deploy:staging
```

#### **2. GitLab CI/CD**
```yaml
# .gitlab-ci.yml
stages:
  - build
  - test
  - deploy

variables:
  NODE_VERSION: "20"

build:
  stage: build
  image: node:${NODE_VERSION}
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/

test:
  stage: test
  image: node:${NODE_VERSION}
  script:
    - npm ci
    - npm run lint
    - npm test
  coverage: '/Coverage: \d+.\d+%/'

deploy_production:
  stage: deploy
  only:
    - main
  script:
    - npm run deploy:production
  environment:
    name: production
    url: https://example.com
```

#### **3. Jenkins** (Still widely used in enterprises)
```groovy
// Jenkinsfile
pipeline {
    agent any
    
    tools {
        nodejs "NodeJS 20"
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'npm ci'
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            parallel {
                stage('Lint') {
                    steps {
                        sh 'npm run lint'
                    }
                }
                stage('Unit Tests') {
                    steps {
                        sh 'npm run test:unit'
                    }
                }
                stage('Integration Tests') {
                    steps {
                        sh 'npm run test:integration'
                    }
                }
            }
        }
        
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                sh 'npm run deploy'
            }
        }
    }
    
    post {
        always {
            junit 'test-results/**/*.xml'
            publishHTML([
                reportDir: 'coverage',
                reportFiles: 'index.html',
                reportName: 'Coverage Report'
            ])
        }
        failure {
            mail to: 'team@example.com',
                 subject: "Build Failed: ${env.JOB_NAME}",
                 body: "Check ${env.BUILD_URL}"
        }
    }
}
```

### Docker Best Practices

```dockerfile
# ✅ Multi-stage build - smaller final image
FROM node:20-alpine AS builder

WORKDIR /app

# Copy package files first (better caching)
COPY package*.json ./
RUN npm ci --only=production

# Copy source code
COPY . .
RUN npm run build

# Production stage
FROM node:20-alpine

WORKDIR /app

# Create non-root user
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

# Copy from builder
COPY --from=builder --chown=nodejs:nodejs /app/dist ./dist
COPY --from=builder --chown=nodejs:nodejs /app/node_modules ./node_modules
COPY --from=builder --chown=nodejs:nodejs /app/package.json ./

# Use non-root user
USER nodejs

# Expose port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s \
  CMD node healthcheck.js

CMD ["node", "dist/index.js"]
```

### Docker Compose Example

```yaml
version: '3.8'

services:
  web:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DB_HOST=postgres
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_started
    restart: unless-stopped
    networks:
      - app-network

  postgres:
    image: postgres:15-alpine
    environment:
      - POSTGRES_DB=myapp
      - POSTGRES_USER=admin
      - POSTGRES_PASSWORD_FILE=/run/secrets/db_password
    volumes:
      - postgres-data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U admin"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - app-network

  redis:
    image: redis:7-alpine
    command: redis-server --appendonly yes
    volumes:
      - redis-data:/data
    networks:
      - app-network

volumes:
  postgres-data:
  redis-data:

networks:
  app-network:
    driver: bridge
```

---

## 🧪 Testing Strategies

### Testing Pyramid

```
        ╱╲
       ╱  ╲      E2E Tests (Few)
      ╱ E2E╲     - Full user flows
     ╱──────╲    - Slow, expensive
    ╱        ╲
   ╱          ╲  Integration Tests (Some)
  ╱Integration╲ - Multiple components
 ╱──────────── ╲ - Moderate speed
╱              ╲
╱  Unit Tests   ╲ Unit Tests (Many)
╱───────────────╲ - Single components
                  - Fast, cheap
```

### Unit Testing

```typescript
// calculator.ts
export class Calculator {
  add(a: number, b: number): number {
    return a + b;
  }

  divide(a: number, b: number): number {
    if (b === 0) {
      throw new Error('Division by zero');
    }
    return a / b;
  }
}

// calculator.test.ts
import { Calculator } from './calculator';

describe('Calculator', () => {
  let calculator: Calculator;

  beforeEach(() => {
    calculator = new Calculator();
  });

  describe('add', () => {
    it('should add two positive numbers', () => {
      expect(calculator.add(2, 3)).toBe(5);
    });

    it('should handle negative numbers', () => {
      expect(calculator.add(-2, 3)).toBe(1);
    });

    it('should handle zero', () => {
      expect(calculator.add(0, 5)).toBe(5);
    });
  });

  describe('divide', () => {
    it('should divide two numbers', () => {
      expect(calculator.divide(10, 2)).toBe(5);
    });

    it('should throw error on division by zero', () => {
      expect(() => calculator.divide(10, 0)).toThrow('Division by zero');
    });

    it('should handle negative results', () => {
      expect(calculator.divide(-10, 2)).toBe(-5);
    });
  });
});
```

### Integration Testing

```javascript
// userService.test.js
import request from 'supertest';
import app from '../app';
import db from '../database';

describe('User API Integration Tests', () => {
  beforeAll(async () => {
    await db.connect();
  });

  afterAll(async () => {
    await db.disconnect();
  });

  beforeEach(async () => {
    await db.clear('users');
  });

  describe('POST /api/users', () => {
    it('should create a new user', async () => {
      const userData = {
        name: 'John Doe',
        email: 'john@example.com'
      };

      const response = await request(app)
        .post('/api/users')
        .send(userData)
        .expect(201);

      expect(response.body).toMatchObject({
        id: expect.any(Number),
        name: userData.name,
        email: userData.email
      });

      // Verify in database
      const user = await db.query('SELECT * FROM users WHERE email = $1', 
        [userData.email]);
      expect(user).toBeDefined();
    });

    it('should return 400 for invalid email', async () => {
      const userData = {
        name: 'John Doe',
        email: 'invalid-email'
      };

      const response = await request(app)
        .post('/api/users')
        .send(userData)
        .expect(400);

      expect(response.body.error).toContain('Invalid email');
    });

    it('should return 409 for duplicate email', async () => {
      const userData = {
        name: 'John Doe',
        email: 'john@example.com'
      };

      // Create first user
      await request(app)
        .post('/api/users')
        .send(userData)
        .expect(201);

      // Try to create duplicate
      const response = await request(app)
        .post('/api/users')
        .send(userData)
        .expect(409);

      expect(response.body.error).toContain('already exists');
    });
  });
});
```

### E2E Testing (Playwright)

```typescript
// tests/e2e/checkout.spec.ts
import { test, expect } from '@playwright/test';

test.describe('Checkout Flow', () => {
  test.beforeEach(async ({ page }) => {
    // Setup: Login and add items to cart
    await page.goto('/login');
    await page.fill('[data-test="email"]', 'test@example.com');
    await page.fill('[data-test="password"]', 'password123');
    await page.click('[data-test="login-button"]');
    
    await expect(page).toHaveURL('/dashboard');
  });

  test('should complete checkout successfully', async ({ page }) => {
    // Add product to cart
    await page.goto('/products/123');
    await page.click('[data-test="add-to-cart"]');
    
    // View cart
    await page.click('[data-test="cart-icon"]');
    await expect(page.locator('[data-test="cart-item"]')).toHaveCount(1);
    
    // Proceed to checkout
    await page.click('[data-test="checkout-button"]');
    
    // Fill shipping information
    await page.fill('[data-test="address"]', '123 Main St');
    await page.fill('[data-test="city"]', 'New York');
    await page.fill('[data-test="zip"]', '10001');
    
    // Fill payment information
    await page.fill('[data-test="card-number"]', '4242424242424242');
    await page.fill('[data-test="card-expiry"]', '12/25');
    await page.fill('[data-test="card-cvc"]', '123');
    
    // Complete purchase
    await page.click('[data-test="place-order"]');
    
    // Verify success
    await expect(page).toHaveURL(/\/order-confirmation/);
    await expect(page.locator('[data-test="success-message"]'))
      .toContainText('Order placed successfully');
  });

  test('should show error for invalid card', async ({ page }) => {
    await page.goto('/checkout');
    
    await page.fill('[data-test="card-number"]', '0000000000000000');
    await page.click('[data-test="place-order"]');
    
    await expect(page.locator('[data-test="error-message"]'))
      .toContainText('Invalid card');
  });
});
```

### Test-Driven Development (TDD)

**Process:**
```
┌──────────┐
│ 1. Write │
│   Test   │ (Red - test fails)
└────┬─────┘
     │
     ▼
┌──────────┐
│ 2. Write │
│   Code   │ (Green - test passes)
└────┬─────┘
     │
     ▼
┌──────────┐
│ 3. Refactor│
│   Code   │ (Improve while keeping tests green)
└────┬─────┘
     │
     └─────────┐
               ▼
          (Repeat)
```

**Example:**
```python
# 1. Write test first
def test_password_validator():
    # Test should fail initially
    assert is_valid_password("short") == False
    assert is_valid_password("NoNumbers!") == False
    assert is_valid_password("nonumbers1") == False
    assert is_valid_password("ValidPass123!") == True

# 2. Write minimal code to pass
def is_valid_password(password):
    if len(password) < 8:
        return False
    if not any(c.isdigit() for c in password):
        return False
    if not any(c.isupper() for c in password):
        return False
    if not any(c in "!@#$%^&*" for c in password):
        return False
    return True

# 3. Refactor for clarity
import re

def is_valid_password(password):
    """
    Password must have:
    - At least 8 characters
    - At least one digit
    - At least one uppercase letter
    - At least one special character
    """
    if len(password) < 8:
        return False
    
    patterns = [
        r'\d',              # digit
        r'[A-Z]',           # uppercase
        r'[!@#$%^&*]'       # special char
    ]
    
    return all(re.search(pattern, password) for pattern in patterns)
```

---

## 🔒 Security Best Practices

### OWASP Top 10 (2025)

#### **1. Broken Access Control**
```javascript
// ❌ Insecure - no authorization check
app.delete('/api/users/:id', async (req, res) => {
  await deleteUser(req.params.id);
  res.send('Deleted');
});

// ✅ Secure - proper authorization
app.delete('/api/users/:id', authenticateUser, async (req, res) => {
  // Check if user is admin OR deleting own account
  if (!req.user.isAdmin && req.user.id !== req.params.id) {
    return res.status(403).json({ error: 'Forbidden' });
  }
  
  await deleteUser(req.params.id);
  res.send('Deleted');
});
```

#### **2. Cryptographic Failures**
```python
# ❌ Weak encryption
import hashlib
password_hash = hashlib.md5(password.encode()).hexdigest()

# ✅ Strong encryption with salt
import bcrypt

# Hashing password
salt = bcrypt.gensalt(rounds=12)
password_hash = bcrypt.hashpw(password.encode(), salt)

# Verifying password
is_valid = bcrypt.checkpw(password.encode(), stored_hash)
```

#### **3. Injection Attacks**
```javascript
// ❌ SQL Injection vulnerable
const query = `SELECT * FROM users WHERE email = '${email}'`;

// ✅ Parameterized queries
const query = 'SELECT * FROM users WHERE email = $1';
const result = await db.query(query, [email]);

// ❌ Command Injection vulnerable
const { exec } = require('child_process');
exec(`convert ${filename} output.jpg`);

// ✅ Safe parameter handling
const { spawn } = require('child_process');
const convert = spawn('convert', [filename, 'output.jpg']);
```

#### **4. Insecure Design**
```typescript
// ❌ No rate limiting
app.post('/api/login', async (req, res) => {
  const user = await authenticate(req.body.email, req.body.password);
  // Attacker can brute force passwords
});

// ✅ Rate limiting implemented
import rateLimit from 'express-rate-limit';

const loginLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 5, // 5 attempts
  message: 'Too many login attempts, please try again later'
});

app.post('/api/login', loginLimiter, async (req, res) => {
  const user = await authenticate(req.body.email, req.body.password);
  if (!user) {
    // Log failed attempt with IP
    await logFailedAttempt(req.ip, req.body.email);
    return res.status(401).json({ error: 'Invalid credentials' });
  }
  // Success
});
```

#### **5. Security Misconfiguration**
```yaml
# ❌ Insecure Docker configuration
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nodejs
COPY . /app
CMD ["node", "server.js"]

# ✅ Secure Docker configuration
FROM node:20-alpine  # Minimal base image
RUN apk --no-cache add ca-certificates  # Only necessary packages

WORKDIR /app

# Run as non-root user
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

COPY --chown=nodejs:nodejs package*.json ./
RUN npm ci --only=production

COPY --chown=nodejs:nodejs . .

USER nodejs  # Switch to non-root user

CMD ["node", "server.js"]
```

### Environment Variables

```bash
# ❌ Committed to repository
# .env file in Git
DATABASE_URL=postgres://admin:password123@localhost:5432/db
API_KEY=sk_live_abc123def456

# ✅ Proper secrets management
# .env.example (committed to Git)
DATABASE_URL=postgres://user:password@localhost:5432/dbname
API_KEY=your_api_key_here

# .env (in .gitignore)
DATABASE_URL=postgres://admin:secure_password@prod-db:5432/prod_db
API_KEY=sk_live_real_key_here

# Use secret managers in production
# AWS Secrets Manager, Azure Key Vault, HashiCorp Vault
```

### HTTPS & Certificate Management

```nginx
# nginx.conf - Force HTTPS
server {
    listen 80;
    server_name example.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name example.com;

    # SSL certificates
    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    # Strong SSL configuration
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;

    # Security headers
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header Content-Security-Policy "default-src 'self'" always;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### Input Validation

```typescript
import { z } from 'zod';

// Define schema
const UserSchema = z.object({
  email: z.string().email().max(255),
  password: z.string().min(8).max(100)
    .regex(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])/,
      'Password must include uppercase, lowercase, number, and special char'),
  age: z.number().int().min(18).max(120),
  website: z.string().url().optional()
});

// Validate input
app.post('/api/users', async (req, res) => {
  try {
    const validatedData = UserSchema.parse(req.body);
    // Process validated data
    const user = await createUser(validatedData);
    res.status(201).json(user);
  } catch (error) {
    if (error instanceof z.ZodError) {
      return res.status(400).json({
        error: 'Validation failed',
        details: error.errors
      });
    }
    throw error;
  }
});
```

---

## 🛠️ Modern Development Tools

### Package Managers

#### **npm / yarn / pnpm**
```bash
# npm (Node Package Manager)
npm install package-name
npm install --save-dev package-name  # Dev dependency
npm update                           # Update packages
npm audit fix                        # Fix vulnerabilities

# yarn (Fast, reliable)
yarn add package-name
yarn add --dev package-name
yarn upgrade
yarn audit

# pnpm (Efficient, disk space saver)
pnpm add package-name
pnpm add --save-dev package-name
pnpm update
pnpm audit
```

### Linters & Formatters

#### **ESLint Configuration**
```json
// .eslintrc.json
{
  "env": {
    "node": true,
    "es2025": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "rules": {
    "no-console": "warn",
    "no-unused-vars": "error",
    "@typescript-eslint/no-explicit-any": "error",
    "max-len": ["error", { "code": 100 }],
    "complexity": ["error", 10]
  }
}
```

#### **Prettier Configuration**
```json
// .prettierrc
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "arrowParens": "avoid"
}
```

### Build Tools

#### **Vite (Modern, Fast)**
```typescript
// vite.config.ts
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  build: {
    minify: 'terser',
    sourcemap: true,
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ['react', 'react-dom'],
          utils: ['lodash', 'axios']
        }
      }
    }
  },
  server: {
    port: 3000,
    proxy: {
      '/api': 'http://localhost:8000'
    }
  }
});
```

#### **Webpack (Configurable, Powerful)**
```javascript
// webpack.config.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name].[contenthash].js',
    clean: true
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env', '@babel/preset-react']
          }
        }
      },
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, 'css-loader']
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html'
    }),
    new MiniCssExtractPlugin({
      filename: '[name].[contenthash].css'
    })
  ],
  optimization: {
    splitChunks: {
      chunks: 'all'
    }
  }
};
```

### Monitoring & Observability

```typescript
// Application monitoring with OpenTelemetry
import { NodeSDK } from '@opentelemetry/sdk-node';
import { getNodeAutoInstrumentations } from '@opentelemetry/auto-instrumentations-node';
import { PrometheusExporter } from '@opentelemetry/exporter-prometheus';

const sdk = new NodeSDK({
  instrumentations: [getNodeAutoInstrumentations()],
  metricReader: new PrometheusExporter({
    port: 9090
  })
});

sdk.start();

// Structured logging
import winston from 'winston';

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.json()
  ),
  transports: [
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' })
  ]
});

// Usage
logger.info('User logged in', {
  userId: user.id,
  ip: req.ip,
  timestamp: new Date().toISOString()
});

logger.error('Payment failed', {
  userId: user.id,
  amount: 100,
  error: err.message,
  stack: err.stack
});
```

---

## 🤖 AI-Powered Development

### GitHub Copilot Best Practices

```javascript
// ✅ Write descriptive comments for better suggestions
// Function to calculate compound interest with monthly contributions
// Parameters: principal (initial), rate (annual), years, monthlyContribution
function calculateInvestmentGrowth(principal, rate, years, monthlyContribution) {
  // Copilot will suggest accurate implementation
}

// ✅ Use clear function names
async function fetchUserProfileWithOrders(userId) {
  // Copilot understands intent from name
}

// ❌ Vague naming
async function getData(id) {
  // Copilot may generate generic code
}
```

### AI Code Review

```yaml
# .github/workflows/ai-review.yml
name: AI Code Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: AI Code Review
        uses: CodeRabbit/action@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          # AI reviews for:
          # - Security vulnerabilities
          # - Performance issues
          # - Best practice violations
          # - Code smells
```

### AI-Assisted Testing

```python
# Using AI to generate test cases
import openai

def generate_test_cases(function_code: str) -> str:
    """
    Use AI to generate comprehensive test cases
    """
    prompt = f"""
    Generate comprehensive unit tests for this function:
    
    {function_code}
    
    Include:
    - Happy path tests
    - Edge cases
    - Error handling
    - Boundary conditions
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    
    return response.choices[0].message.content

# Example usage
code = """
def divide(a: int, b: int) -> float:
    return a / b
"""

test_cases = generate_test_cases(code)
print(test_cases)
```

### Responsible AI Usage

**Guidelines:**
- ✅ Review all AI-generated code
- ✅ Test thoroughly
- ✅ Understand what the code does
- ✅ Check for security vulnerabilities
- ✅ Verify licensing compatibility
- ❌ Don't blindly accept suggestions
- ❌ Don't use for sensitive/proprietary code
- ❌ Don't rely on AI for critical decisions

---

## 📖 Quick Reference

### Software Development Lifecycle (SDLC)

```
1. Requirements ──▶ 2. Design ──▶ 3. Implementation
     ▲                                      │
     │                                      ▼
6. Maintenance ◀── 5. Deployment ◀── 4. Testing
```

### Agile Ceremonies

**Sprint Planning** → Set goals and tasks  
**Daily Standup** → 15-min sync (What did you do? What will you do? Blockers?)  
**Sprint Review** → Demo completed work  
**Retrospective** → Improve processes

### Code Review Checklist

- [ ] Code follows style guide
- [ ] Tests are included and pass
- [ ] No security vulnerabilities
- [ ] Performance is acceptable
- [ ] Error handling is proper
- [ ] Documentation is updated
- [ ] No code duplication
- [ ] Names are clear and meaningful
- [ ] Functions are small and focused
- [ ] No commented-out code

### Performance Optimization

**Frontend:**
- Lazy loading
- Code splitting
- Image optimization
- Caching strategies
- Minification
- CDN usage

**Backend:**
- Database indexing
- Query optimization
- Caching (Redis, Memcached)
- Load balancing
- Async processing
- Connection pooling

### Common HTTP Status Codes

```
Success:
200 OK - Request succeeded
201 Created - Resource created
204 No Content - Success, no response body

Client Errors:
400 Bad Request - Invalid request
401 Unauthorized - Authentication required
403 Forbidden - Authenticated but not authorized
404 Not Found - Resource doesn't exist
409 Conflict - Conflict with current state
422 Unprocessable Entity - Validation failed

Server Errors:
500 Internal Server Error - Generic error
502 Bad Gateway - Invalid response from upstream
503 Service Unavailable - Temporary overload
504 Gateway Timeout - Upstream timeout
```

### API Design Best Practices

```
✅ RESTful Principles:
GET    /api/users          # List users
GET    /api/users/123      # Get specific user
POST   /api/users          # Create user
PUT    /api/users/123      # Update user (full)
PATCH  /api/users/123      # Update user (partial)
DELETE /api/users/123      # Delete user

✅ Use plural nouns
✅ Use HTTP methods correctly
✅ Version your API (/api/v1/)
✅ Use proper status codes
✅ Implement pagination
✅ Support filtering & sorting
✅ Provide clear error messages
```

### Database Best Practices

```sql
-- ✅ Use indexes for frequently queried columns
CREATE INDEX idx_users_email ON users(email);

-- ✅ Use foreign keys for referential integrity
ALTER TABLE orders
ADD CONSTRAINT fk_user_id
FOREIGN KEY (user_id) REFERENCES users(id);

-- ✅ Use transactions for related operations
BEGIN TRANSACTION;
  UPDATE accounts SET balance = balance - 100 WHERE id = 1;
  UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;

-- ✅ Avoid SELECT *
SELECT id, name, email FROM users WHERE active = true;

-- ✅ Use prepared statements (prevents SQL injection)
PREPARE get_user AS SELECT * FROM users WHERE id = $1;
EXECUTE get_user(123);
```

### Microservices Communication

```
┌─────────────┐
│   Service A │
└──────┬──────┘
       │
       ├──── Synchronous ────▶ REST API / gRPC
       │
       └──── Asynchronous ───▶ Message Queue (RabbitMQ, Kafka)
```

### Deployment Strategies

**Blue-Green Deployment:**
```
Blue (Current) ──┐
                 ├──▶ Router ──▶ Users
Green (New) ─────┘
(Switch when ready)
```

**Canary Deployment:**
```
V1 (90%) ──┐
           ├──▶ Load Balancer ──▶ Users
V2 (10%) ──┘
(Gradually increase V2 traffic)
```

**Rolling Deployment:**
```
Server 1: V1 → V2 → ✓
Server 2: V1 ──→ V2 → ✓
Server 3: V1 ────→ V2 → ✓
(Update one at a time)
```

---

## 🎓 Learning Resources

### Books
- "Clean Code" - Robert C. Martin
- "Design Patterns" - Gang of Four
- "The Pragmatic Programmer" - Hunt & Thomas
- "Refactoring" - Martin Fowler
- "Domain-Driven Design" - Eric Evans

### Online Platforms
- [GitHub](https://github.com) - Code hosting
- [Stack Overflow](https://stackoverflow.com) - Q&A
- [MDN Web Docs](https://developer.mozilla.org) - Web standards
- [FreeCodeCamp](https://freecodecamp.org) - Tutorials
- [Codecademy](https://codecademy.com) - Interactive learning

### Communities
- r/programming - Reddit community
- Dev.to - Developer articles
- Hacker News - Tech news
- Discord servers - Real-time chat
- Local meetups - In-person networking

---

## 💡 Final Tips

### Continuous Learning
- 🔄 Technology changes rapidly - stay updated
- 📚 Read code from open-source projects
- 🏗️ Build side projects to experiment
- 👥 Join developer communities
- 🎯 Focus on fundamentals, not just frameworks

### Work-Life Balance
- 🧘 Avoid burnout - take breaks
- 🌳 Step away from the screen
- 💪 Exercise regularly
- 😴 Get adequate sleep
- 🤝 Maintain social connections

### Career Growth
- 📝 Write technical blog posts
- 🎤 Give talks at meetups
- 🌟 Contribute to open source
- 🤝 Mentor junior developers
- 🎓 Pursue certifications strategically

---

## 🔗 Useful Commands Cheat Sheet

### Terminal Shortcuts
```bash
# Navigation
ctrl + a    # Move to start of line
ctrl + e    # Move to end of line
ctrl + u    # Delete to start of line
ctrl + k    # Delete to end of line
ctrl + r    # Search command history

# Process management
ctrl + c    # Terminate process
ctrl + z    # Suspend process
jobs        # List background jobs
fg %1       # Bring job 1 to foreground
```

### Git Shortcuts
```bash
# Aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'

# Usage
git co main       # checkout main
git st            # status
git last          # show last commit
```

### Docker Commands
```bash
# Container management
docker ps                    # List running containers
docker ps -a                 # List all containers
docker stop <container>      # Stop container
docker rm <container>        # Remove container
docker logs <container>      # View logs

# Image management
docker images                # List images
docker rmi <image>           # Remove image
docker pull <image>          # Download image
docker build -t name .       # Build image

# Cleanup
docker system prune          # Remove unused data
docker volume prune          # Remove unused volumes
```

### npm/yarn Commands
```bash
# Package management
npm install / yarn           # Install dependencies
npm install -g <pkg>         # Global install
npm uninstall <pkg>          # Remove package
npm update                   # Update packages
npm outdated                 # Check outdated packages

# Scripts
npm run build                # Build project
npm run test                 # Run tests
npm run dev                  # Start dev server
npm run lint                 # Run linter

# Security
npm audit                    # Check vulnerabilities
npm audit fix                # Auto-fix vulnerabilities
```

---

**Last Updated:** December 2025

**Version:** 1.0

**License:** MIT

---

> 💡 **Remember:** Great software engineering is not about knowing everything, but about knowing how to find answers, learning continuously, and writing code that others (including future you) can understand and maintain.

Happy coding! 🚀