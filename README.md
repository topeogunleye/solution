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

1. **Create an `.nvmrc` File**:

   - Navigate to the root directory of your project using a terminal or command prompt.
   - Create a new file named `.nvmrc`. You can do this by running the following command:
     ```
     echo "20.12.2" > .nvmrc
     ```
   - This will set the desired Node.js version (in this case, 20.12.2) for your project.

2. **Automatic Version Switching**:
   - Once you've created and saved the `.nvmrc` file, you need to ensure that nvm (Node Version Manager) automatically loads the specified version when you enter your project directory.
   - To achieve this, add the following lines to your shell configuration file (e.g., `.bashrc`, `.zshrc`, or `.profile`):

```bash
load_nvmrc() {
local node_version="$(nvm version)"
local nvmrc_path="$(nvm_find_nvmrc)"
if [ -n "$nvmrc_path" ]; then
  local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")
  if [ "$nvmrc_node_version" = "N/A" ]; then
    nvm install
  elif [ "$nvmrc_node_version" != "$node_version" ]; then
    nvm use
  fi
elif [ "$node_version" != "$(nvm version default)" ]; then
  echo "Reverting to nvm default version"
  nvm use default
fi
}

# Call the function when the shell starts or when the current directory changes
load_nvmrc
```

- This configuration ensures that nvm checks the `.nvmrc` file and switches to the specified Node.js version automatically when you enter your project directory.

That's it! Now your project will use Node.js version 20.12.2 whenever you work within its directory. If you have any further questions or need additional assistance, feel free to ask! 🚀¹²³⁴⁵


````
Source: Conversation with Bing, 5/18/2024
(1) How to write a .nvmrc file which automatically change node version. https://stackoverflow.com/questions/57110542/how-to-write-a-nvmrc-file-which-automatically-change-node-version.
(2) How to Write an Nvmrc File for Automatic Node Version Change. https://www.squash.io/how-to-write-an-nvmrc-file-for-automatic-node-version-change/.
(3) Mastering Node.js Versions with NVM | by Rokstack | Medium. https://medium.com/@rokstack/mastering-node-js-versions-with-nvm-191602d7f3dd.
(4) Change project, Change node version let .nvmrc help you. https://thawinwats.medium.com/change-project-change-node-version-let-nvmrc-help-you-630b34dafd09.
(5) How to automatically manage Node versions - Matt Fantinel. https://fantinel.dev/automatically-manage-node-versions.
(6) github.com. https://github.com/luizaoformiga/chatbot-telegram/tree/2f15ac5f58e0e5d74b5e10f2761f6d27c79fcc3d/README.md.
(7) github.com. https://github.com/inventer99/swrc/tree/039e9b3335e2585f81c0fe005f6590084860c12a/plugins%2Fnvm%2F_plugin.sh.