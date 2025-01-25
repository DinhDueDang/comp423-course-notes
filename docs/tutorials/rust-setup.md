# Setting up a dev container for Rust

* Primary author: [Dinh Dang](https://github.com/DinhDueDang)
* Reviewer: [Joseph Pham](https://github.com/jhpham)

## Prerequisites

1. Git: Used as a tool for modern source code management. Download and install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). 
2. Visual Studio Code (VS Code): An integrated development environment that assists with code writing. Download and install [VS Code](https://code.visualstudio.com/).
3. GitHub Account: A cloud based platform to host repositories. Create an account or log into [Github](https://github.com/). 
4. Docker: A tool to helpp automate the deployment of applications. Download and install [Docker](https://www.docker.com/products/docker-desktop/).

## **Creating a new Dev Container in Rust**

### Step 1: Create a New Project Directory

1. Open terminal

2. Create a new directory:  
    ```
    mkdir <name-of-new-project>
    cd <name-of-new-project> 
    ```

2. Initialize a Git Repository:  
    ```
    git init  
    ```

### Step 2: Create a Dev Container for Rust

1. In VS Code open the <name-of-new-project> directory. You can do this via: File > Open Folder.

2. Install "Dev Container" in the extension portion of VS Code

3. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:
    ```  
    .devcontainer/devcontainer.json
    ```

4. In this devcontainer file we define the configuration for our development environment. Add this to devcontainer.json
```
{
    "name": "Rust Dev Container",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "extensions": [
                "rust-lang.rust-analyzer"
            ]
        }
    },
    "postCreateCommand": "cargo install cargo-edit"
}
```

- ```name```: The name of the Dev Container project
- ```image```: The official Rust Dev Container image which is given by Microsoft
- ```customizations.vscode.extensions```: Ensures that the Rust extension is downloaded
- ```postCreateCommand```: runs the ```cargo install cargo-edit``` command after the container is started so the user has access to it if they need

### Step 3: Open the Project in the Dev Container

Reopen the container by using the command palette (Ctrl+Shift+P or Cmd+Shift+P on macOS) and select: **Dev Containers: Reopen in Container**. 

Once the new Dev Container is setup, close out of the current terminal and open a new terminal tab within VS Code and inputting ```rustc --version``` to see if the container is running the newest version of Rust.

### Step 4: Initialize a new Rust Module

