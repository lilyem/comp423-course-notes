# Setting up a dev container for Rust

* Primary author: [Lily Moore](https://github.com/lilyem)
* Reviewer: [Colby Eagan](https://github.com/colbyeagan)

## Objectives

In this tutorial, you will learn how to set up a project from scratch in the Rust Programming language! By the conclusion, you will have created a project that prints "Hello COMP423."

## Prerequisites

In order to complete this tutorial, make sure you have:

* A GitHub Account
* Git installed
* Visual Studio Code (VS Code)
* Docker Installed

## Part 1. Project Setup: Creating the Repository

### Step 1. Create a Local Directory and Initialize Git

1) Open your terminal or command prompt.

2) Navigate to the dirrectory in which you would like this tutorial to go, then create a new directory for your project by running the following code:  

``` shell
mkdir comp423-rust-tutorial
cd comp423-rust-tutorial
```

3) Initialize a new Git repository:

``` shell
git init
```

4) Create a README file:

``` shell
echo "# COMP423 Rust tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2. Create a Remote Repository on GitHUb

1) Log in to your GitHub and go to the [Create a New Repository](https://github.com/new) page. 

2) Fill in the details as follows:

* **Repository name:** `comp-423-rust-tutorial`
* **Description:** "Practice setting up a dev container for Rust"
* **Visibility:** Public

3) You do not need to initialise the repository with a README, .gitignore, or license.

4) Click **Create Repository**

### Step 3. Link your Local Repository to GitHub

1) Add the GitHub repository as a remote:

``` shell
git remote add origin https://github.com/<your-username>/comp-423-rust-tutorial.git # (1)!
```

1.  make sure to replace `<your-username>` with your GitHub username.

2) Check your default branch name with the subcommand `git branch`. If it is not already `main`, rename it to `main` by running `git branch -M main`. 

