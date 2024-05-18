# Troubleshooting Guide: Fixing "No preset version installed for command npm"

## Problem Description
When running `npm install`, you encountered the error message:
```
No preset version installed for command npm
Please install a version by running one of the following:

asdf install nodejs 18

or add one of the following versions in your config file at /home/t/.tool-versions
nodejs 20.11.0
nodejs 20.12.2
nodejs 20.9.0
```

This guide explains how to resolve this issue step by step.

## Solution Steps

### 1. Check Node.js Installation
First, verify that Node.js is installed correctly on your system. Open a terminal and run:
```bash
node -v
```
This command should print the version number of Node.js if it's installed correctly.

### 2. Install npm Globally
If npm is missing, you can install it globally by running:
```bash
npm install -g npm
```

### 3. Update .tool-versions File
The error message mentions a `.tool-versions` file. This file is used by version managers like `asdf`. Make sure you have this file in your home directory (`/home/t/`) and that it includes the desired Node.js version. For example:
```plaintext
nodejs 20.12.2
```

### 4. Set Global Node.js Version Using asdf
If you're using `asdf`, set the global Node.js version by running:
```bash
asdf global nodejs 20.12.2
```

### 5. Reshim asdf Binaries (if needed)
If you're still encountering issues, try reshimming the asdf binaries:
```bash
asdf reshim
```

### 6. Check Environment Variables
Ensure that your environment variables (such as `$PATH`) are correctly set up to include the path to Node.js and npm.

Remember to adjust the version numbers according to your requirements. If you're using a different version of Node.js, replace `20.12.2` with the desired version.

---

Feel free to customize this documentation for your specific project. If you have any further questions, don't hesitate to ask! 😊👍