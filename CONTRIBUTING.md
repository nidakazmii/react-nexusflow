# Contributing to React-NexusFlow

Thank you for your interest in contributing to React-NexusFlow! We welcome contributions from developers of all skill levels. This document provides guidelines and instructions for contributing to the project.

## Code of Conduct

We are committed to providing a welcoming and inclusive environment for all contributors. Please be respectful and considerate in all interactions.

## Getting Started

### Prerequisites
- Node.js >= 18.x
- npm, pnpm, or yarn
- Git
- Basic knowledge of React and TypeScript

### Setting Up Your Development Environment

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/react-nexusflow.git
   cd react-nexusflow
   ```
3. **Add upstream remote** to keep your fork synced:
   ```bash
   git remote add upstream https://github.com/nidakazmii/react-nexusflow.git
   ```
4. **Install dependencies**:
   ```bash
   npm install
   ```
5. **Start the development server**:
   ```bash
   npm run dev
   ```

## Development Workflow

### Creating a Feature Branch

Always create a new branch for your work:

```bash
git checkout -b feature/your-feature-name
```

Use descriptive branch names:
- `feature/` for new features
- `fix/` for bug fixes
- `docs/` for documentation updates
- `refactor/` for code refactoring
- `perf/` for performance improvements

### Making Changes

1. **Write clear, maintainable code** following the project's conventions
2. **Add tests** for new functionality and bug fixes
3. **Update documentation** if your changes affect user-facing features
4. **Keep commits atomic** - each commit should represent a logical unit of work

### Commit Messages

Write clear, descriptive commit messages:

- Use the imperative mood ("Add feature" not "Added feature")
- Keep the first line under 50 characters
- Provide additional context in the body if needed
- Reference related issues (e.g., "Fixes #123")

Example:
```
Add validation for circular dependencies in graph

This adds a pre-flight check to detect circular dependency loops
before executing the workflow.

Fixes #42
```

### Running Tests

Before submitting a PR, ensure all tests pass:

```bash
# Run the entire test suite
npm run test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode (useful during development)
npm run test -- --watch
```

We aim for high code coverage (94%+). Your changes should maintain or improve this coverage.

### Code Quality

The project uses linting and formatting tools. Make sure your code passes quality checks:

```bash
# Format code (if available)
npm run format

# Lint code (if available)
npm run lint
```

## Architecture Guidelines

When contributing, please be familiar with the core architectural patterns:

### 1. Decoupled Reactive State Layer
- Keep the logical graph schema separate from React components
- Use Zustand + Immer for state management
- Components should subscribe only to specific node or edge slices

### 2. Command Pattern
- Encapsulate user interactions as serialized commands
- Ensure all mutations are immutable and reversible
- Support undo/redo functionality

### 3. Plugin API
- Follow the Open-Closed principle
- New node types and edge renderers should use the defined API contract
- Avoid modifying core logic for extensions

## Submitting Changes

### Before Creating a Pull Request

1. **Sync with upstream**: 
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```
2. **Run tests** to ensure everything passes
3. **Review your own changes** before requesting review

### Creating a Pull Request

1. **Push your branch** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
2. **Open a Pull Request** on GitHub with:
   - A clear, descriptive title
   - A detailed description of the changes
   - Reference to related issues (if applicable)
   - A summary of testing done

3. **PR Title Format**: Follow the same convention as commits
   - `feature:` for new features
   - `fix:` for bug fixes
   - `docs:` for documentation
   - `refactor:` for refactoring

### PR Description Template

```markdown
## Description
Brief summary of the changes

## Changes
- Change 1
- Change 2
- Change 3

## Type of change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
Describe the testing you've done

## Related Issues
Fixes #(issue number)
```

## Review Process

- At least one maintainer review is required
- Address feedback promptly and push updates to the same PR
- CI checks must pass before merging
- Keep discussions constructive and focused on the code

## Reporting Bugs

Found a bug? Please create an issue with:

1. **Title**: Clear description of the problem
2. **Description**: Detailed explanation with context
3. **Steps to Reproduce**: Clear steps to reproduce the issue
4. **Expected vs Actual Behavior**: What should happen vs what happens
5. **Environment**: OS, Node version, etc.
6. **Screenshots/Code Samples**: If applicable

## Feature Requests

Have an idea for a new feature?

1. Check existing issues to avoid duplicates
2. Open an issue with:
   - Clear title and description
   - Use case and expected behavior
   - Any relevant design considerations
3. Discuss with maintainers before starting implementation

## Documentation Contributions

Documentation improvements are always welcome:

- Update README for setup/usage changes
- Add code comments for complex algorithms
- Create examples for new features
- Improve existing documentation for clarity

## Performance Considerations

When contributing, keep performance in mind:

- Avoid unnecessary re-renders
- Use React's performance optimization features (memo, useCallback, useMemo)
- Profile your changes with the provided tools:
  ```bash
  npm run build && npm run preview -- --profile
  ```
- Test with large graph datasets (thousands of nodes)

## Licensing

By contributing to React-NexusFlow, you agree that your contributions will be licensed under the MIT License.

## Questions?

- Check the README for architectural overview
- Review existing code and tests for patterns
- Open a discussion issue for questions
- Reach out to maintainers for guidance

## Thank You!

Your contributions make React-NexusFlow better. We appreciate your time and effort!
