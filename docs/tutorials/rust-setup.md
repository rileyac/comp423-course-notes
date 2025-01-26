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
(D) Create a README file:
```
echo "# Setting up a dev container for Rust" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a Remote Repository on GitHub
(1) Log in to your GitHub account and navigate to the Create a New Repository page.

(2) Fill in the details as follows:

* Repository Name: rust-tutorial
* Description: "Following a tutorial for setting up a dev container for Rust and writing a simple "Hello COMP423 Program."
* Visibility: Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click **Create Repository.**

### Step 3: Link your Local Repository to GitHub



