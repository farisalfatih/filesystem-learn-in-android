# Contributing to Linux Filesystem Commands Learning Repository

Thank you for your interest in contributing to this educational project! We welcome contributions from everyone, whether you're fixing a typo, adding examples, or creating new lessons.

## How to Contribute

### Types of Contributions

We appreciate all kinds of contributions:

- **Documentation improvements:** Fix typos, clarify explanations, add examples
- **New exercises:** Create practice problems and scenarios
- **Code examples:** Add practical shell script examples
- **Translations:** Translate lessons to other languages
- **Issue reports:** Report errors, unclear content, or suggest improvements
- **Reviews:** Review and test existing content

### Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/filesystem-learn-in-android.git
   cd filesystem-learn-in-android
   ```
3. **Create a branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Making Changes

#### For Documentation/Content

1. **Keep it clear and concise:** Use simple language
2. **Include examples:** Show practical usage
3. **Test your examples:** Make sure commands work as described
4. **Follow existing format:** Match the style of existing lessons
5. **Add exercises:** Include practice exercises when relevant

#### For Code Examples

1. **Comment your code:** Explain what it does
2. **Keep it simple:** Use basic commands that work across distributions
3. **Test thoroughly:** Ensure examples work in common Linux environments
4. **Follow best practices:** Use safe commands and proper error handling

### Content Guidelines

#### Writing Style

- Use clear, beginner-friendly language
- Define technical terms when first used
- Include both explanation and examples
- Add warnings for potentially dangerous commands
- Use consistent formatting

#### Command Examples

- Show the command and its expected output
- Use realistic examples
- Include common use cases
- Warn about dangerous operations (e.g., `rm -rf`)
- Test commands before submitting

#### Example Format

```bash
# Good example format:
$ command --option argument
expected output
```

### Lesson Structure

Each lesson should include:

1. **Learning Objectives:** What students will learn
2. **Commands Covered:** List of main commands
3. **Detailed Explanations:** How each command works
4. **Examples:** Practical usage demonstrations
5. **Exercises:** Practice problems
6. **Tips and Best Practices:** Pro tips and common mistakes
7. **Command Cheat Sheet:** Quick reference
8. **Next Steps:** Link to the next lesson

### Submitting Changes

1. **Commit your changes** with clear messages:
   ```bash
   git add .
   git commit -m "Add: exercise for file permissions"
   ```

2. **Push to your fork:**
   ```bash
   git push origin feature/your-feature-name
   ```

3. **Open a Pull Request:**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your branch
   - Fill in the PR template

### Pull Request Guidelines

#### PR Title

Use clear, descriptive titles:
- `Add: new exercise for grep command`
- `Fix: typo in navigation lesson`
- `Update: chmod examples in permissions lesson`
- `Docs: improve README installation section`

#### PR Description

Include:
- What changes you made
- Why you made them
- Any relevant issue numbers
- Testing you performed

#### Before Submitting

- [ ] Read through your changes
- [ ] Test all command examples
- [ ] Check for typos and grammar
- [ ] Follow the existing style
- [ ] Update table of contents if needed
- [ ] Add yourself to contributors list (if major contribution)

### Code of Conduct

#### Be Respectful

- Be welcoming to newcomers
- Be patient with questions
- Provide constructive feedback
- Assume good intentions

#### Be Helpful

- Explain your suggestions
- Link to relevant resources
- Share your knowledge
- Help review other PRs

### Reporting Issues

When reporting issues, please include:

1. **Clear description:** What's wrong or what you'd like to see
2. **Location:** Which lesson/section/file
3. **Expected vs actual:** What you expected vs what you found
4. **Suggestions:** If you have ideas for fixes
5. **Environment:** If relevant (OS, shell version, etc.)

### Suggesting New Content

For new lessons or major additions:

1. **Open an issue first** to discuss the idea
2. **Outline the structure** you're proposing
3. **Explain the value** for learners
4. **Get feedback** before investing time in writing
5. **Submit in stages** if it's a large addition

### Translation Guidelines

If translating to another language:

1. Create a new directory: `lessons-[language-code]/`
2. Maintain the same structure as English version
3. Adapt examples to be culturally relevant
4. Keep technical terms consistent
5. Update main README with language links

### Style Guide

#### Formatting

- Use code blocks for commands and output
- Use `inline code` for commands in sentences
- Use **bold** for emphasis
- Use *italic* sparingly
- Use tables for structured information

#### Command Presentation

```bash
# Good: Shows prompt, command, and output
$ ls -la
total 16
drwxr-xr-x 2 user user 4096 Jan  1 10:00 Documents

# Avoid: No context or output
ls -la
```

#### Warnings

Always warn about dangerous operations:

```bash
⚠️ **Warning:** This command will delete all files!
$ rm -rf *
```

### Testing Your Changes

Before submitting:

1. **Test all commands** in a safe environment
2. **Check all links** to ensure they work
3. **Review formatting** in Markdown preview
4. **Verify examples** produce expected output
5. **Read through** as if you're a beginner

### Questions?

- Open an issue for questions
- Tag maintainers if needed
- Check existing issues/PRs for similar topics
- Be patient waiting for responses

### Recognition

Contributors will be recognized in:
- Pull request acknowledgments
- Release notes (for significant contributions)
- Contributors section (for ongoing contributors)

### License

By contributing, you agree that your contributions will be licensed under the same license as this project (see LICENSE file).

---

## Quick Contribution Checklist

- [ ] Forked and cloned the repository
- [ ] Created a descriptive branch name
- [ ] Made changes following style guidelines
- [ ] Tested all command examples
- [ ] Checked spelling and grammar
- [ ] Committed with clear messages
- [ ] Pushed to your fork
- [ ] Opened a pull request with good description

---

## Thank You!

Every contribution, no matter how small, helps make this resource better for learners around the world. We appreciate your time and effort!

Happy contributing! 🚀
