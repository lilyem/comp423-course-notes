# Setting up a dev container for Rust

* Primary author: [Lily Moore](https://github.com/lilyem)
* Reviewer: [Colby Eagan](https://github.com/colbyeagan)

## Objectives

In this tutorial, you will learn how to set up a project from scratch in the Rust Programming language! By the conclusion, you will have set up a Development container (and learn about why these are important!) and created a project that prints "Hello COMP423" in Rust.

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

!!! note
    Older versions of `git` choose the name `master`, however, we will use the name `main` because that is the standpard primary branch name these days.

3) Push your local commits to the GitHub repository by running:

``` shell
git push --set-upstream origin main # (1)!
```

1. This command pushes the main branch to the remote repository origin.

4) In GitHub on your web browser, refresh and you should now see the same local commit you made has been pushed to remote!

## Part 2. Setting Up the Development Environment for Rust

!!! info "Development Containers"
    A development(dev) container is a preconfigured environment that makes sure that your development environment is consistent. Dev containers are defined by a set of files and usually use Docker to create isolated setups. This is important because it allows everyone to work in an identical environment which reduces bugs and simplifies onboarding new members.

### Step 1. Add Development Container Configuration

1. In VS Code, open the `comp-423-rust-tutorial` directory. You can do this by clicking File, then Open Folder.

2) Install the Dev container extension for VS Code.

3) Create a `.devcontainer` directory in the root of your project with the file `.devcontainer/devcontainer.json` inside of this "hidden" configuration directory.

!!! Tip ""
    This file defines the configuration for your development environment. It will specify the name, image, and customizations for your dev container.

In this file put the following:
``` json
{
  "name": "COMP423 Rust Tutorial",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  }
}
```
Step 2. Reopen the Project in a VSCode Dev Container

Reopen the project in the container by pressing `Ctrl+Shift+P` or if you are on a Mac `Cmd+Shift+P`, then type "Dev Containers: Reopen in Container" and select that option. This may take a few minutes to install and dowload everything. Once this completes, you can close the current terminal tab.

Step 3. Open a new terminal tab in VSCode and try running `rustc --version` to see your dev container is running a recent version of rust!

## Part 3. Creating a new Rust Project

[Rust](https://www.rust-lang.org/learn) is the programming language we have installed through the dev container we just set up, and what language we will be writing our "Hello COMP43" in. In Rust, a *crate* is an executable program. Rather than simply complining our crates usinf the Rust compiler, `rustc`, we will be using [Cargo](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html) in this tutprial. Cargo is the package manager for Rust and does the following:

* Runs `rustc`

* Creates two metadata files

* Builds and fetches your package's depentencies

* Simplifies workong with Rust packes via normalizing commands

1) Use the `cargo new` command to start a new package with Cargo, and specify that we want to create a binary project. This will automatically make a new git repo which we do not want to do here, so use the `--vsc none` flag. Open the terminal in your VSCode dev container you just set up and run the following:
``` shell
cargo new hello_comp423 --bin --vcs none 
cd hello_comp423
```

!!! info ""
    The `--vsc none` flag does not create a new `git` repository automatically on your behalf. The `--bin` flag means that we are making a binary program.

You should now see a `hello_comp423` directory. Click on this to see the files that the `cargo new` command created.

!!! note "Cargo.toml"
    The `Cargo.toml` file is called a manifest and it contains data written in TOML format that Cargo uses to compile your package.

2) Now, open `src/main.rs`, and modify its contents to be:

``` rust
fn main() {
    println!("Hello COMP423");
}
```

3) To complile and run the program, you can do one of two things: use `cargo build` to compile your program, and and then run your program using its file path, or simply use `cargo run` to both complie and run your program with one command.

* Compile and run in two steps:

``` rust
cargo build
./target/debug/hello_comp423
```
!!! info "cargo build and gcc"
    Rust's `cargo build` is similar to C's `gcc` in that they compile the program without running it.


* Use `cargo run` to compile and run in one step.

You should try compliling and running your program with both of these methods for practice. Notice that both produce the same output:
```
   Compiling hello_comp423 v0.1.0 (/workspaces/comp423-rust-tutorial/hello_comp423)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.32s
Hello COMP423
```

Now that you have set up your dev container and written a "Hello COMP423", you should stage, commit, and push your work to GitHub! Remeber to use `git push origin main` when pushing your changes.

To learn more about [Rust](https://www.rust-lang.org/learn) and [Cargo](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html), check out their documentation linked here!


#### References

[1] K. Jordan, “Starting a static website project with MkDocs,” COMP423, [https://comp423-25s.github.io/resources/MkDocs/tutorial/#step-2-add-requirementstxt-python-dependency-configuration](https://comp423-25s.github.io/resources/MkDocs/tutorial/#step-2-add-requirementstxt-python-dependency-configuration) (accessed Jan. 25, 2025). 
