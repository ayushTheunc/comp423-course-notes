# Setting up a dev container for Rust

* Primary author: [Ayush Pai](https://github.com/ayushTheunc)
* Reviewer: [Max Yu](https://github.com/myu123)

## Prerequisites

Before starting, ensure you have the following installed on your system:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)
- [Dev Containers extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Step-by-Step Instructions

### Step 1: Create a New Project Directory

1. Open your terminal and create a new directory for your Rust project:
   ```bash
   mkdir rust-project
   cd rust-project
   ```
2. Initialize a new Git repository locally:
   ```bash
   git init
   echo "# Rust Project" > README.md
   git add README.md
   git commit -m "Initial commit with README"
   ```

### Step 2: Create a Remote Repository and Link It

1. Go to [GitHub](https://github.com/) and create a new repository named `rust-project`.
2. Do not initialize the repository with a README, .gitignore, or license.
3. Back in your terminal, add the remote repository to your local Git repository:
   ```bash
   git remote add origin https://github.com/YourGitHubUsername/rust-project.git
   ```
4. Push your initial commit to GitHub:
   ```bash
   git branch -M main
   git push -u origin main
   ```

### Step 3: Configure the Development Container in VS Code

1. Open the project in VS Code by selecting **File > Open Folder** and navigating to your `rust-project` directory.
2. In the Explorer pane, right-click and select **New Folder**, then name it `.devcontainer`.
3. Inside the `.devcontainer` folder, create a new file named `devcontainer.json` and add the following content:
   ```json
   {
     "name": "Rust Dev Container",
     "image": "mcr.microsoft.com/vscode/devcontainers/rust:latest",
     "customizations": {
       "vscode": {
         "extensions": ["rust-lang.rust-analyzer"]
       }
     }
   }
   ```
4. Use the integrated terminal (Ctrl+` or View > Terminal) to add and commit the new files:
   ```bash
   git add .devcontainer
   git commit -m "Add dev container configuration"
   ```

#### Explanation of the `devcontainer.json` file

- **`name`**: Specifies the name of the dev container, making it easy to identify in VS Code.
- **`image`**: Defines the base Docker image used for the development environment. Here, it specifies a Rust development image provided by Microsoft.
- **`customizations`**: Customizes VS Code settings for the container. The example enables the Rust extension for better Rust language support.

### Step 4: Open the Dev Container in VS Code

1. From the Command Palette:
   - **Windows/Linux**: Press `Ctrl+Shift+P`.
   - **Mac**: Press `Cmd+Shift+P`.
2. Select **Reopen in Container**.
3. Wait for the container to build and initialize.

### Step 5: Initialize a Rust Project in the Dev Container

1. Inside the integrated terminal in VS Code, verify your Rust installation by checking the version:
   ```bash
   rustc --version
   ```
   Ensure the displayed version is recent and supported.

2. Initialize a new Rust module:
   ```bash
    cargo new helloCOMP423 --bin --vcs none
   ```

3. Inside the helloWorldCOMP423 directory, modify the file `main.rs` with the following content:
   ```rust
   fn main() {
       println!("Hello, COMP423!");
   }
   ```


### Step 6: Compile and Run the Project in the Dev Container

1. Compile the project:
   ```bash
    cargo build

   ```
   This generates a binary file named `helloWorldCOMP423`. The `cargo build` command is similar to the `gcc` command in C programming (as used in COMP211). Like `gcc`, `carbo build` compiles your source code into a executable file which doesn't need a Rust Environment to run. 

2. Run and Compile the compiled binary directly:
   ```bash
   cargo run
   ```
   You should see:
   ```
   Hello COMP423
   ```
   Unlike cargo build, cargo run both compiles and runs the main.rs file. If you just want to run the file after it is compiled by cargo build, 
   use ./target/debug/hello_world, assuming you are in the same directory as the main.rs file. 


   **Key Difference**: `cargo build` creates a reusable binary file, whereas `cargo run` executes the program directly without saving a binary.

### Step 7: Push Updates to GitHub from VS Code

1. Add and commit the Rust project files:
   ```bash
   git add .
   git commit -m "Add basic Rust project with Hello COMP423"
   ```

2. Push the latest changes to GitHub using the integrated terminal:
   ```bash
   git push
   ```

## Final Steps

Congratulations! Your Rust project is now set up with a dev container and linked to a GitHub repository.

For additional help, consult the [official Rust documentation](https://www.rust-lang.org/learn).