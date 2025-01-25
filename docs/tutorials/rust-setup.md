# Setting up a dev container for Rust

* Primary author: [Ayush Pai](https://github.com/ayushTheunc)
* Reviewer: [Max Yu](https://github.com/myu123)

## Prerequisites

Before starting, ensure you have the following installed on your system:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)
- [Dev Containers extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

!!! note
    Ensure all prerequisites are properly installed before proceeding. Missing any of these tools may lead to issues later.

---

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

!!! tip
    Use meaningful commit messages to help keep your repository organized and easy to navigate.

---

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

!!! warning
    Be cautious when pasting your GitHub repository URL. Make sure it is correct to avoid linking to the wrong repository.

---

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

!!! info
    The `devcontainer.json` file specifies the configuration for your development environment, including the base image (`rust:latest`) and the VS Code extension for Rust.

---

### Step 4: Open the Dev Container in VS Code

1. From the Command Palette:
   - **Windows/Linux**: Press `Ctrl+Shift+P`.
   - **Mac**: Press `Cmd+Shift+P`.
2. Select **Reopen in Container**.
3. Wait for the container to build and initialize.

!!! warning
    Ensure Docker is running before reopening in the container. Otherwise, VS Code will not be able to build the container.

---

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

!!! note
    The `--bin` flag creates a binary (executable) Rust project, and `--vcs none` prevents Cargo from initializing a new Git repository.

3. Inside the `helloCOMP423` directory, modify the file `main.rs` with the following content:
   ```rust
   fn main() {
       println!("Hello, COMP423!");
   }
   ```

!!! tip
    Use the Rust `println!` macro to print text to the console. The `!` signifies it is a macro, not a regular function.

---

### Step 6: Compile and Run the Project in the Dev Container

1. Compile the project:
   ```bash
   cargo build
   ```
   This generates a binary file in the `target/debug/` directory. The `cargo build` command is similar to the `gcc` command in C programming (as used in COMP211). Like `gcc`, `cargo build` compiles your source code into an executable file that does not require the Rust environment to run.

!!! success
    If the compilation is successful, you’ll find the compiled binary in the `target/debug/` directory.

2. Run the compiled binary directly:
   ```bash
   ./target/debug/helloCOMP423
   ```
   You should see:
   ```
   Hello COMP423
   ```

3. Alternatively, use the following command to compile and run in one step:
   ```bash
   cargo run
   ```

!!! question
    Why use `cargo build` over `cargo run`?  
    Use `cargo build` if you plan to run the binary multiple times. It saves time by avoiding repeated compilation.

   **Key Difference**: `cargo build` creates a reusable binary file, whereas `cargo run` compiles and executes the program in a single step.

---

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

!!! tip
    Regularly push your changes to keep your GitHub repository up to date.

---

## Final Steps

Congratulations! Your Rust project is now set up with a dev container and linked to a GitHub repository.

!!! info
    For additional help, consult the [official Rust documentation](https://www.rust-lang.org/learn).
