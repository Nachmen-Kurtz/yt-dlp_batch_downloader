# Contributing to YT-DLP Batch Downloader

<!--toc:start-->
- [Contributing to YT-DLP Batch Downloader](#contributing-to-yt-dlp-batch-downloader)
  - [📋 Table of Contents](#📋-table-of-contents)
  - [🤝 Code of Conduct](#🤝-code-of-conduct)
  - [💡 How Can I Contribute?](#💡-how-can-i-contribute)
    - [1. **Report Bugs** 🐛](#1-report-bugs-🐛)
    - [2. **Suggest Features** ✨](#2-suggest-features)
    - [3. **Write Code** 💻](#3-write-code-💻)
    - [4. **Improve Documentation** 📚](#4-improve-documentation-📚)
    - [5. **Test** 🧪](#5-test-🧪)
    - [6. **Translate** 🌍](#6-translate-🌍)
  - [🚀 Getting Started](#🚀-getting-started)
    - [Prerequisites](#prerequisites)
    - [Setting Up Development Environment](#setting-up-development-environment)
  - [🛠 Development Guidelines](#🛠-development-guidelines)
    - [Code Quality Standards](#code-quality-standards)
    - [Testing Checklist](#testing-checklist)
    - [Key Areas for Contribution](#key-areas-for-contribution)
  - [📤 Submitting Changes](#📤-submitting-changes)
    - [Pull Request Process](#pull-request-process)
    - [Pull Request Guidelines](#pull-request-guidelines)
  - [🐛 Reporting Bugs](#🐛-reporting-bugs)
    - [Before Submitting](#before-submitting)
    - [Bug Report Template](#bug-report-template)
  - [✨ Suggesting Features](#suggesting-features)
    - [Feature Request Template](#feature-request-template)
    - [Good Feature Requests](#good-feature-requests)
  - [📝 Style Guidelines](#📝-style-guidelines)
    - [Bash Script Style](#bash-script-style)
    - [Documentation Style](#documentation-style)
  - [🏆 Recognition](#🏆-recognition)
  - [📞 Getting Help](#📞-getting-help)
  - [📄 License](#📄-license)
  - [🙏 Thank You!](#🙏-thank-you)
<!--toc:end-->

Thank you for your interest in contributing to YT-DLP Batch Downloader! 🎉

We welcome contributions from everyone. This document provides guidelines to help you contribute effectively.

---

## 📋 Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [How Can I Contribute?](#how-can-i-contribute)
3. [Getting Started](#getting-started)
4. [Development Guidelines](#development-guidelines)
5. [Submitting Changes](#submitting-changes)
6. [Reporting Bugs](#reporting-bugs)
7. [Suggesting Features](#suggesting-features)
8. [Style Guidelines](#style-guidelines)

---

## 🤝 Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment:

- **Be respectful**: Value different perspectives and experiences
- **Be constructive**: Offer helpful feedback and criticism
- **Be patient**: Remember that everyone is learning
- **Be collaborative**: Work together to improve the project
- **No harassment**: Zero tolerance for harassment or discrimination

---

## 💡 How Can I Contribute?

There are many ways to contribute:

### 1. **Report Bugs** 🐛

Found a bug? Let us know! See [Reporting Bugs](#reporting-bugs) section.

### 2. **Suggest Features** ✨

Have an idea for improvement? See [Suggesting Features](#suggesting-features) section.

### 3. **Write Code** 💻

Submit patches, bug fixes, or new features via pull requests.

### 4. **Improve Documentation** 📚

Help us improve README, comments, or create tutorials.

### 5. **Test** 🧪

Test the script on different platforms and report issues.

### 6. **Translate** 🌍

Help translate error messages or documentation to other languages.

---

## 🚀 Getting Started

### Prerequisites

- Basic knowledge of Bash scripting
- Git installed on your system
- yt-dlp installed (`pip install yt-dlp`)
- A GitHub account (for submitting contributions)

### Setting Up Development Environment

1. **Fork the repository**

   ```bash
   # Click the "Fork" button on GitHub
   ```

2. **Clone your fork**

   ```bash
   git clone https://github.com/YOUR_USERNAME/yt-dlp-batch-downloader.git
   cd yt-dlp-batch-downloader
   ```

3. **Create a branch for your changes**

   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b bugfix/issue-description
   ```

4. **Make the script executable**

   ```bash
   chmod +x yt-dlp_downloader.sh
   ```

5. **Test your changes**

   ```bash
   ./yt-dlp_downloader.sh test_urls.txt
   ```

---

## 🛠 Development Guidelines

### Code Quality Standards

1. **Test thoroughly**: Test all changes on Linux and macOS if possible
2. **Follow existing patterns**: Maintain consistency with current code style
3. **Add comments**: Explain complex logic or non-obvious decisions
4. **Handle errors**: Always include proper error handling
5. **Preserve backward compatibility**: Don't break existing functionality

### Testing Checklist

Before submitting, verify:

- [ ] Script runs without errors on fresh URLs
- [ ] Script handles invalid URLs correctly
- [ ] Script handles network failures gracefully
- [ ] Script handles missing files appropriately
- [ ] Batch file update works correctly
- [ ] Summary report displays accurate information
- [ ] Colors display correctly in terminal
- [ ] Subtitles are downloaded and embedded (v2.0+)
- [ ] Chapters are preserved in videos (v2.0+)

### Key Areas for Contribution

**High Priority:**

- Resume support for interrupted downloads
- Parallel download implementation
- Enhanced error recovery mechanisms
- Performance optimizations

**Medium Priority:**

- Quality selection options
- Audio-only mode
- Configuration file support
- Additional subtitle languages

**Documentation:**

- Video tutorials
- Usage examples
- Troubleshooting guide
- FAQ section

---

## 📤 Submitting Changes

### Pull Request Process

1. **Update documentation**
   - Update README.md if you add features
   - Add entry to CHANGELOG.md under [Unreleased]
   - Update comments in code

2. **Commit your changes**

   ```bash
   git add .
   git commit -m "Add feature: Brief description"
   ```

   **Commit Message Format:**

   ```
   <type>: <subject>
   
   <body (optional)>
   
   <footer (optional)>
   ```

   **Types:**
   - `feat`: New feature
   - `fix`: Bug fix
   - `docs`: Documentation changes
   - `style`: Code style changes (formatting)
   - `refactor`: Code refactoring
   - `test`: Adding tests
   - `chore`: Maintenance tasks

   **Examples:**

   ```
   feat: Add support for quality selection
   
   fix: Handle empty batch file correctly
   
   docs: Update installation instructions
   ```

3. **Push to your fork**

   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create Pull Request**
   - Go to your fork on GitHub
   - Click "New Pull Request"
   - Provide clear description of changes
   - Reference any related issues

5. **Respond to feedback**
   - Address reviewer comments
   - Make requested changes
   - Push updates to same branch

### Pull Request Guidelines

Your PR should:

- ✅ Have a clear, descriptive title
- ✅ Reference related issues (`Fixes #123`)
- ✅ Include testing details
- ✅ Update relevant documentation
- ✅ Pass all existing tests
- ✅ Follow code style guidelines
- ✅ Include only related changes

---

## 🐛 Reporting Bugs

### Before Submitting

1. **Check existing issues**: Search for similar reports
2. **Verify it's a bug**: Ensure it's not expected behavior
3. **Test with latest version**: Update yt-dlp and try again
4. **Isolate the problem**: Create minimal reproduction case

### Bug Report Template

```markdown
**Description**
A clear description of the bug.

**Steps to Reproduce**
1. Run command '...'
2. With batch file containing '...'
3. See error

**Expected Behavior**
What should happen.

**Actual Behavior**
What actually happens.

**Environment**
- OS: [e.g., Ubuntu 22.04]
- Bash version: [e.g., 5.1.16]
- yt-dlp version: [e.g., 2023.12.30]
- Script version: [e.g., 2.0.0]

**Batch File Content**
```

<https://example.com/video1>
<https://example.com/video2>

```

**Error Output**
```

[Paste error messages here]

```

**Additional Context**
Any other relevant information.
```

---

## ✨ Suggesting Features

### Feature Request Template

```markdown
**Feature Description**
Clear description of the proposed feature.

**Use Case**
Why is this feature needed? What problem does it solve?

**Proposed Solution**
How should this feature work?

**Alternatives Considered**
What other solutions did you consider?

**Additional Context**
Mockups, examples, or related features.
```

### Good Feature Requests

- Solve a real problem
- Are clearly described
- Consider edge cases
- Don't break existing features
- Are feasible to implement

---

## 📝 Style Guidelines

### Bash Script Style

1. **Indentation**: 2 spaces (no tabs)

   ```bash
   if [ condition ]; then
     echo "Indented with 2 spaces"
   fi
   ```

2. **Variable naming**: UPPERCASE for constants, lowercase for locals

   ```bash
   DOWNLOAD_DIR="/path/to/dir"  # Constant
   file_count=0                 # Variable
   ```

3. **Quotes**: Always quote variables

   ```bash
   echo "$VAR"           # Correct
   echo $VAR             # Incorrect
   ```

4. **Functions**: Use descriptive names with underscores

   ```bash
   download_video() {
     # Function implementation
   }
   ```

5. **Error handling**: Check command success

   ```bash
   if ! command -v yt-dlp &>/dev/null; then
     echo "Error: yt-dlp not found"
     exit 1
   fi
   ```

6. **Comments**: Explain why, not what

   ```bash
   # Good: Extract title for progress tracking
   TITLE=$(yt-dlp --get-title "$URL")
   
   # Bad: Get title
   TITLE=$(yt-dlp --get-title "$URL")
   ```

### Documentation Style

- Use clear, concise language
- Include code examples
- Add emoji for visual clarity (sparingly)
- Test all command examples
- Keep line length under 100 characters

---

## 🏆 Recognition

Contributors will be recognized in:

- README.md Contributors section
- Release notes for significant contributions
- Project documentation

---

## 📞 Getting Help

Need help contributing?

- **Questions**: Open a GitHub Discussion
- **Clarifications**: Comment on relevant issues
- **Chat**: Join our community chat (if available)

---

## 📄 License

By contributing, you agree that your contributions will be licensed under the GPL v3+ License.

---

## 🙏 Thank You

Every contribution, no matter how small, helps make this project better. We appreciate your time and effort!

Happy coding! 🚀
