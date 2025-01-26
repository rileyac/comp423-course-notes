# Setting up a dev container for Rust

* Primary author: [Riley Chapman](https://github.com/rileyac)

* Reviewer: [Sarah Glenn](https://github.com/skglenn07)

## Introduction

Welcome! In this tutorial you will learn how to set up a basic project from scratch in Rust. By the end of this guide, you'll have set up a new dev container for Rust, created a new project, and written a basic "Hello COMP423" program. We are going to start from a blank repository which will help you learn the fundamentals of project setup and configuration. 

### Why This Matters

Development containers (dev containers) are a way to set up consistent and reproducible development environments. This ensures everything works the same for everyone, which is super helpful when collaborating with others or learning something new. This fixes the "but it works on my computer" issue. Plus, knowing how to set a project up from scratch is a great way to build confidence and learn the basics of Rust!

## Prerequisites
(Taken from the [COMP 423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial))

Before we begin, make sure you have the following:

1. A GitHub account: If you don’t have one yet, sign up at [GitHub.](https://github.com/)

2. Git installed: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.

3. Visual Studio Code (VS Code): Download and install it from [here.](https://code.visualstudio.com/)

4. Docker installed: Required to run the dev container. Get Docker [here.](https://www.docker.com/products/docker-desktop)

5. Command-line basics

## Part 1: Creating Git Repository
(Taken from the [COMP 423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial))

### Step 1: Create a Local Directory and Initialize Git
(A) Open your terminal

(B) Create a new directory for your project:

```
mkdir rust-tutorial
cd rust-tutorial
```
(C) Initialize a new git repsitory:
```
git init
```
!!! note
    This command creates a new, empty Git repository! This will allow you to track changes and versions of your project. 

(D) Create a README file:
```
echo "# Setting up a dev container for Rust" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a Remote Repository on GitHub
(1) Log in to your GitHub account and navigate to the Create a New Repository page.

(2) Fill in the details as follows:

* **Repository Name:** rust-tutorial
* **Description:** "Following a tutorial for setting up a dev container for Rust and writing a simple "Hello COMP423 Program."
* **Visibility:** Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click **Create Repository.**

### Step 3: Link your Local Repository to GitHub
(1) Add the GitHub repository as a remote:
```
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```
Replace ```<your-username>``` with your GitHub username.

(2) Check your default branch name with the subcommand ```git branch```. If it's not ```main```, rename it to ```main``` with the following command: ```git branch -M main```. Old versions of git choose the name ```master``` for the primary branch, but these days ```main``` is the standard primary branch name.

(3) Push your local commits to the GitHub repository:
```
git push --set-upstream origin main
```

(4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use git log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

## Part 2: Setting Up the Development Environment
(References [COMP 423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial))
### Step 1: Add Development Container Configuration
1. In VS Code, open the ```rust-tutorial``` directory. You can do this via: File > Open Folder.
2. Install the **Dev Containers extension** for VS Code.
3. Create a ```.devcontainer``` directory in the root of your project with the following file inside of this "hidden" configuration directory: ```.devcontainer/devcontainer.json```

The ```devcontainer.json``` file defines the configuration for your development environment. Here, we're specifying the following:

* **name:** A descriptive name for your dev container.
* **image:** The Docker image to use, in this case, the latest version of a Rust environment. We are going to use one of Microsoft's base images.
* **customizations:** Adds useful configurations to VS Code, like installing the Rust Analyzer extension.

```
{
  "name": "Rust Dev Container",
  "image": "rust:latest",  
  "customizations": {
    "vscode": {
      "settings": {
        "rust-analyzer.cargo.runBuildScripts": true,
        "rust-analyzer.procMacro.enable": true
      },
      "extensions": [
        "rust-lang.rust-analyzer"
      ]
    }
  }
}
```

### Step 2: Reopen the Project in a VSCode Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.

When you open the project in VS Code, it will automatically pull the Rust Docker image, set up the environment, and install the necessary extensions. This ensures you have a consistent and reproducible Rust development setup every time. It might take a minute to load.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running ```rustc --version``` to see your dev container is running a recent version of Rust with little effort!

## Part 3: Creating and Running a "Hello COMP423" Program in Rust
Now that you’ve set up your dev container and initialized a Git repository, let’s write a simple "Hello COMP423" program in Rust.

### Step 1: Create a New Rust Project

To create a new Rust project, we are going to use **Cargo**. Cargo is Rust's package manager and build system, similar to **pip** for Python. Run the following command in the terminal within your dev container:
```
cargo new hello-comp423 --vcs none

```

* ```cargo new hello-comp423``` creates a new project named ```hello-comp423```.
* ```--vcs none``` ensures that Cargo does not automatically initialize a Git repository for this project, leaving version control to be managed separately or manually later.

This will create a new directory called ```hello-comp423```, with the following default files:

* ```Cargo.toml```: The manifest file for the project, where dependencies and other project metadata are specified.
* ```src/main.rs```: The default entry point for your program.

### Step 2: Edit the ```src/main.rs``` File
Open ```src/main.rs``` in VSCode and replace the contents with the following code:
```
fn main() {
    println!("Hello COMP423");
}
```
This code is a simple Rust program that prints "Hello COMP423" to the terminal when run.

### Step 3: Build the Project Using Cargo

Now that you’ve written the program, you need to **build** it. Rust uses **Cargo** to build projects. After ```cd```-ing into your newly created ```hello-comp423``` directory, run the following command to compile the project:
```
cargo build
```

* This command will compile the project and generate an executable file.
* By default, this output is put in the ```target/debug directory```. The filename will be the same as the project.

### Step 4: Run the Project Using Cargo
You can use the cargo run command to compile and run the project in one step:
```
cargo run
```

??? question
    **What's the difference between ```cargo build``` and ```cargo run```?**
    
    * ```cargo build```: Only compiles the project and outputs the executable, but does not run it.
    * ```cargo run```: Compiles (if necessary) and then runs the project in one command.

## Summary
At this point, you should have seen "Hello COMP423" print in your terminal! Congratulations on finishing the tutorial! To review, you have learned how to:
* Set up a new dev container for Rust
* Initialize a new Git Repository
* Create a new project in Rust
* Write, compile, and run a simple "Hello COMP 423" program in Rust
