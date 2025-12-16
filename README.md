# LyraJS

[![npm version](https://img.shields.io/npm/v/create-lyrajs)](https://www.npmjs.com/package/create-lyrajs)
[![CLA Assistant](https://cla-assistant.io/readme/badge/devway-eu/lyrajs)](https://cla-assistant.io/devway-eu/lyrajs)
[![docs](https://img.shields.io/badge/docs-read-green)](https://lyrajs.dev)
[![Discord](https://img.shields.io/discord/1449345012604342427?label=discord&logo=discord&logoColor=white)](https://discord.gg/cWvUh8pQNU)


LyraJS is a lightweight and modern, developer-friendly TypeScript framework for building robust APIs. It's designed to accelerate API development and provides a comprehensive set of tools including an ORM system, code generation CLI, authentication middleware, and more.

## Core Features

- **TypeScript-First** - Fully typed with excellent IDE support and type safety
- **Built-in ORM** - Decorator-based entities, repositories, and query builder for MySQL
- **Powerful CLI** - Code generation for entities, controllers, migrations, and more
- **Authentication** - JWT-based auth with role-based access control (RBAC)
- **Express Integration** - Built on Express.js for familiar middleware and routing
- **Email Support** - Integrated Nodemailer for transactional emails
- **Migration System** - Version control for your database schema
- **Configuration** - YAML-based configuration with environment support
- **Error Handling** - HTTP exceptions and centralized error handling
- **Developer Experience** - Hot reload, intuitive API, and helpful error messages

## Quick Start

### Create a New Project

Initialize a new LyraJS project:

```bash
# Create a new project (interactive)
npm create lyrajs
# or
npx create-lyrajs

# Follow the prompts:
# Project name: my-api

# Navigate to your project
cd my-api

# Install dependencies
npm install
```

### Project Setup

1. **Configure your database** in `.env`:
   ```env
   # Database configuration
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=your_password
   DB_NAME=my_database

   # JWT configuration
   JWT_SECRET=your-secret-key-here
   JWT_SECRET_REFRESH=your-refresh-secret-key-here

   # Application configuration
   NODE_ENV=dev
   HOST=localhost
   PORT=3333
   CLIENT_APP_URL=http://localhost:5173
   ```

2. **Create your database:**
   ```bash
   npx maestro create:database
   ```

3. **Run migrations:**
   ```bash
   npx maestro migration:migrate
   ```

4. **Start developing:**
   ```bash
   npm run dev
   ```

Your API will be available at `http://localhost:3333/api`

## Project Structure

A typical LyraJS project follows this structure:

```
my-project/
├── src/
├── config/                # YAML configuration files
│   ├── database.yaml      # Database connection config
│   ├── router.yaml        # Routing base path config
│   ├── security.yaml      # JWT & access control config
│   ├── parameters.yaml    # Global app parameters
│   └── mailer.yaml        # Email service config
├── migrations/            # SQL migration files
│   ├── controller/        # HTTP request handlers
│   │   ├── AuthController.ts
│   │   └── UserController.ts
│   ├── entity/            # Database models with decorators
│   │   └── User.ts
│   ├── fixtures/          # Seed data for testing
│   │   └── AppFixtures.ts
│   ├── middleware/        # Custom middleware functions
│   │   └── YourMiddleware.ts
│   ├── repository/        # Database access layer
│   │   └── UserRepository.ts
│   ├── router/            # Route definitions
│   │   ├── index.ts
│   │   └── routes/
│   │       ├── authRoutes.ts
│   │       └── userRoutes.ts
│   ├── services/          # Business logic services
│   │   └── YourService.ts
│   ├── tests/             # Test files
│   │   └── exemple.test.ts
│   ├── types/             # TypeScript type definitions
│   │   └── ExempleType.ts
│   └── server.ts          # Application entry point
├── .env                   # Environment variables
├── package.json
└── tsconfig.json
```

## Maestro CLI Commands

LyraJS provides a powerful CLI (`maestro`) for scaffolding and database management:

```bash
# Database Operations
npx maestro create:database        # Create database from .env config
npx maestro make:migration         # Generate SQL migration from entities
npx maestro migration:migrate      # Execute latest migration

# Code Generation
npx maestro make:entity            # Interactive entity generator
npx maestro make:controller        # Interactive controller generator
npx maestro make:routes            # Interactive route generator

# Data Management
npx maestro fixtures:load          # Load fixture data from AppFixtures.ts

# Introspection
npx maestro show:entities          # List all entities
npx maestro show:controllers       # List all controllers
npx maestro show:repositories      # List all repositories
npx maestro show:routes            # Display route table
npx maestro show:migrations        # List all migrations

# Help
npx maestro                        # Display help with all commands
```

**Interactive Wizards:**

All `make:*` commands provide interactive prompts to guide you through:
- Entity properties, types, constraints, and relations
- Controller types (entity-based CRUD, blank with methods, or minimal)
- Route HTTP methods and paths for each controller action

## Configuration

LyraJS uses YAML configuration files with environment variable interpolation:

### Database Configuration (`config/database.yaml`)

```yaml
database:
  host: "%env(DB_HOST)%"
  port: "%env(DB_PORT)%"
  user: "%env(DB_USER)%"
  password: "%env(DB_PASSWORD)%"
  name: "%env(DB_NAME)%"
```

### Router Configuration (`config/router.yaml`)

```yaml
router:
  base_path: /api  # All routes will be prefixed with /api
```

### Parameters Configuration (`config/parameters.yaml`)

```yaml
parameters:
  api_name: "LyraJS API"
  api_version: "1.0.0"
  api_host: "%env(HOST)%"
  api_port: "%env(PORT)%"
  api_env: "%env(NODE_ENV)%"
```

### Accessing Configuration

```typescript
import { Config } from '@lyra-js/core';

const config = new Config();
const apiName = config.get('parameters.api_name');
const basePath = config.get('router.base_path');
```



## Complete Workflow Example

Here's a typical workflow for creating a new resource in LyraJS:

```bash
# 1. Create entity
npx maestro make:entity
# Enter: Product
# Define fields: name (varchar), price (decimal), description (text)

# 2. Generate migration
npx maestro make:migration

# 3. Run migration
npx maestro migration:migrate

# 4. Create controller
npx maestro make:controller
# Select: Entity based
# Choose: Product

# 5. Create routes
npx maestro make:routes
# Select: ProductController
# Define HTTP methods for each action

# 6. Test your API
npm run dev
# Access: http://localhost:3333/api/product/all
```

## Documentation

- **[Core Framework Documentation](./lyrajs-core/README.md)** - Detailed API reference and advanced features
- **[Template Documentation](./lyrajs-template/README.md)** - Starter template guide and examples
- **[Official Documentation Website](https://lyrajs.dev)** - Complete guides and tutorials

## Repository Structure

This is the main LyraJS repository, organized as a monorepo with Git submodules:

```
lyrajs/
├── lyrajs-core/              # Core framework library (@lyra-js/core on npm)
└── lyrajs-template/          # Project starter template
```

### For Contributors: Working with Submodules

Each submodule is an independent Git repository:

- **[lyrajs-core](https://github.com/devway-eu/lyrajs-core)** - The core framework
- **[lyrajs-template](https://github.com/devway-eu/lyrajs-template)** - Starter template

#### Cloning for Development

```bash
# Clone with all submodules
git clone --recursive https://github.com/devway-eu/lyrajs.git
cd lyrajs

# Or initialize submodules after cloning
git submodule update --init --recursive
```

#### Making Changes

```bash
# Navigate to the submodule
cd lyrajs-core

# Create a feature branch
git checkout -b feature/my-feature

# Make changes and commit
git add .
git commit -m "Add new feature"
git push origin feature/my-feature

# Open a PR in the submodule repository
```

#### Updating Submodule References

```bash
# After changes are merged, update the reference
cd lyrajs-core
git pull origin main

cd ..
git add lyrajs-core
git commit -m "Update lyrajs-core to latest"
git push
```

#### Building and Testing Locally

```bash
# Build the core framework
cd lyrajs-core
npm install
npm run build

# Link it locally for testing
npm link

# In your test project
cd /path/to/your/test-project
npm link @lyra-js/core

# Test your changes
npm run dev
```

## Contributing

We welcome contributions to LyraJS! Here's how you can help:

1. **Fork the specific repository** you want to contribute to (core or template)
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes** and commit: `git commit -m "Add amazing feature"`
4. **Push to your fork**: `git push origin feature/amazing-feature`
5. **Open a Pull Request** in the respective repository

Please read the following before contributing:
- [Contributing Guidelines](./lyrajs-core/CONTRIBUTING.md)
- [Contributor License Agreement](./lyrajs-core/CLA.md)

### Development Workflow

1. Clone the main repository with submodules
2. Make changes in the appropriate submodule
3. Test your changes locally
4. Submit a PR to the submodule repository
5. After merge, update the main repository reference

## Project Status

- **lyrajs-core**: v1.0.0 - Stable
- **lyrajs-template**: Check individual repository for status

## Links

- **Main Repository**: [github.com/devway-eu/lyrajs](https://github.com/devway-eu/lyrajs)
- **Core Repository**: [github.com/devway-eu/lyrajs-core](https://github.com/devway-eu/lyrajs-core)
- **Template Repository**: [github.com/devway-eu/lyrajs-template](https://github.com/devway-eu/lyrajs-template)
- **Documentation Website**: [lyrajs.dev](https://lyrajs.dev)
- **npm Package**: [npmjs.com/package/@lyra-js/core](https://www.npmjs.com/package/@lyra-js/core)

## Support

- **Issues**: Report issues in the specific repository ([core](https://github.com/devway-eu/lyrajs-core/issues) or [template](https://github.com/devway-eu/lyrajs-template/issues))
- **Discussions**: Use GitHub Discussions for questions and ideas

## License

LyraJS is licensed under the [GPL-3.0 License](./lyrajs-core/LICENSE).

## Authors

- Matthieu Fergola
- Anthony Dewitte

---

Built with dedication by the Devway team.

## Contributors ❤️

![Contributors](https://img.shields.io/github/contributors/devway-eu/lyrajs)
