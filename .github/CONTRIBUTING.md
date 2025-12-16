# Contributing to LyraJS

Thank you for your interest in contributing to LyraJS! 🎉

LyraJS is a TypeScript framework for building APIs with ORM, CLI tools, and authentication. This repository serves as the umbrella project for all LyraJS components.

## Project Structure

LyraJS consists of multiple repositories:

- **[@lyrajs/core](https://github.com/devway-eu/lyrajs-core)** - Core framework with ORM, Maestro CLI, and authentication
- **[create-lyrajs](https://github.com/devway-eu/lyrajs-template)** - Project scaffolding tool (`npm create lyrajs`)
- **[lyrajs.dev](https://github.com/devway-eu/lyrajs-documentation)** - Documentation website
- **lyrajs** (this repo) - Umbrella repository for general issues and discussions

## How to Contribute

### Reporting Issues

Choose the right repository for your issue:

- **Core framework bugs/features**: [lyrajs-core issues](https://github.com/devway-eu/lyrajs-core/issues)
- **Template bugs/features**: [lyrajs-template issues](https://github.com/devway-eu/lyrajs-template/issues)
- **Documentation issues**: [lyrajs-documentation issues](https://github.com/devway-eu/lyrajs-documentation/issues)
- **General questions/discussions**: [Use this repo's discussions](https://github.com/devway-eu/lyrajs/discussions)
- **Cross-cutting concerns**: [Use this repo's issues](https://github.com/devway-eu/lyrajs/issues)

### Contributing Code

Depending on what you want to contribute:

1. **Core Framework (ORM, CLI, Auth)**
   - Repository: [lyrajs-core](https://github.com/devway-eu/lyrajs-core)
   - See: [Core Contributing Guide](https://github.com/devway-eu/lyrajs-core/blob/main/.github/CONTRIBUTING.md)

2. **Project Template**
   - Repository: [lyrajs-template](https://github.com/devway-eu/lyrajs-template)
   - See: [Template Contributing Guide](https://github.com/devway-eu/lyrajs-template/blob/main/.github/CONTRIBUTING.md)

3. **Documentation**
   - Repository: [lyrajs-documentation](https://github.com/devway-eu/lyrajs-documentation)
   - Website: [lyrajs.dev](https://lyrajs.dev)

### Contributing to This Repository

This repository is for:
- Overall project coordination
- Cross-component issues
- General discussions about LyraJS
- Community resources
- Project governance

If you're contributing here:

1. Fork this repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Submit a pull request
5. Sign the CLA when prompted

## Code of Conduct

Please be respectful, constructive, and professional in all interactions. We're building a welcoming community for everyone.

## Getting Started

### For Users

Get started with LyraJS:

```bash
# Create a new project
npm create lyrajs

# Or install the core framework
npm install @lyrajs/core
```

### For Contributors

Choose the component you want to contribute to and follow its setup guide:

- [Core Framework Setup](https://github.com/devway-eu/lyrajs-core#development)
- [Template Setup](https://github.com/devway-eu/lyrajs-template#development)
- [Documentation Setup](https://github.com/devway-eu/lyrajs-documentation#development)

## Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>
```

**Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

**Scopes**: `core`, `template`, `docs`, `ci`, `meta`

**Examples**:
```
feat(core): add PostgreSQL support
fix(template): correct .env.example configuration
docs: update getting started guide
chore(ci): update GitHub Actions workflow
```

## Pull Request Process

1. Ensure your PR is in the correct repository
2. Fill out the PR template completely
3. Link related issues
4. Sign the CLA (automated prompt)
5. Wait for review (may take a few days)
6. Address review feedback
7. Maintain your PR until merged

## Community

### Getting Help

- **Documentation**: https://lyrajs.dev/docs
- **Discussions**: https://github.com/devway-eu/lyrajs/discussions
- **Email**: matthieu@dev-way.eu

### Stay Connected

- Watch repositories for updates
- Follow releases
- Join discussions
- Share your projects built with LyraJS!

## Recognition

Contributors are automatically added to CONTRIBUTORS.md in their respective repositories when PRs are merged.

## License

By contributing to LyraJS, you agree to the terms in our [CLA](CLA.md). Your contributions will be licensed under the GPL-3.0 License.

## Helpful Links

- [LyraJS Website](https://lyrajs.dev)
- [Documentation](https://lyrajs.dev/docs)
- [npm Package (@lyrajs/core)](https://www.npmjs.com/package/@lyrajs/core)
- [npm Package (create-lyrajs)](https://www.npmjs.com/package/create-lyrajs)

---

**Questions?** Open a [discussion](https://github.com/devway-eu/lyrajs/discussions) or contact matthieu@dev-way.eu

Thank you for contributing to LyraJS! 🚀
