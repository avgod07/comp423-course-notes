# Setting up a dev container for Go

* Primary author: [Ayush Godhani](https://github.com/avgod07)
* Reviewer: [Prasun Sapkota](https://github.com/psap2)

Hello! In this tutorial we will learn how to set up a dev container for Go. By the end of this tutorial you will have created a Go Development Container in VS Code, making development much easier.

Citation: A lot of the material in this tutorial was directly reused from Kris Jordan's [Starting a Static Website Project with MkDocs](https://comp423-25s.github.io/resources/MkDocs/tutorial/) website. Specifically instructions for the Prerequisites, Part One, and Part Two were reused from the website and amended to fit the necessities of this tutorial. 



## Prerequisites
1. A GitHub account
1. Git installed
1. Visual Studio Code (VS Code)
1. Docker installed

## Part 1: Project Setup: Creating a Repository

### Step 1. Create a Local Directory and Initialize Git

1. Open your terminal or command prompt
1. Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.)
   ```
   mkdir go-tutorial
   cd go-tutorial
   ```
1. Initialize a new Git repository:
   ```
   git init
   ```
1. Create a README file
   ```bash
   echo "# Setting up Dev Container for Hello World! in Go" > README.md
   echo "Full tutorial for [Go Setup Tutorial](https://avgod07.github.io/comp423-course-notes/tutorials/go-setup/)." >> README.md
   git add README.md
   git commit -m "Initial commit with README"
   ```

### Step 2. Create a Remote Repository in Github
1. Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.
1. Fill in the details as follows:
   * **Repository Name**: `go-tutorial`
   * **Description**: "A quick tutorial on how to create a dev container with go and run a simple hello comp423 program"
   * **Visibility**: Public
1. Do not initialize the repository with a README, .gitignore, or license.
1. Click **Create Repository**

### Step 3. Link your Local Repository to GitHub
1. Add the GitHub repository as a remote:
  ```
  git remote add origin https://github.com/<your-username>/go-tutorial.git
  ```
Replace `<your-username>` with your GitHub username.
1. Push your local commits to the GitHub repository:
  ```
  git push --set-upstream origin main
  ```
1. Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. 


## Part 2. Setting Up the Development Environment

### Step 1. Add Development Container Configuration
1. In VS Code, open the `go-tutorial` directory. You can do this via: File > Open Folder.
1. Install the Dev Containers extension for VS Code.
1. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

   `devcontainer/devcontainer.json`

   The `devcontainer.json` file defines the configuration for your development environment. Here, we're specifying the following:

   ```json
      {
         "name": "Go Tutorial Walk Through",
         "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
         "customizations": {
         "vscode": {
            "settings": {},
            "extensions": ["golang.go"]
            }
         }
      }
   ```

!!! info "Why use Dev Containers?"

    Dev containers provide a fully configured development environment with all the tools and settings pre-installed. 
    This makes sures that everyone working on the project has an identical setup, which helps in reducing "works on my machine" problems.

### Step 2. Reopen the Project in a VSCode Dev Container
Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Lets quickly make sure that the dev container was set up correctly and check what version of Go was installed.

1. Open your terminal in vscode and insert the following command:
```
go version
```
Now you should see that a recent version of Go was installed, meaning that your dev container was set up properly. 

## Part 3. Your First Go Program (Hello Comp423)

### Step 1. Create Go Module

In order to do this, run the following command in your terminal:

```
go mod init go-tutorial
```

This should create your go module which is required for your application to run. Go modules are used to manage dependencies and ensure that the correct versions of libraries and packages are used. I like to think of this module like a requirements.txt file, although it does have it's differences.

### Step 2. Create a New Go File

Make a new file in your go-tutorial directory called `main.go`.

### Step 3. Write Your First Go Program
This following program will print Hello COMP423:
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
### Step 4. Run Your Program
In your vscode terminal copy and paste the command below:
```
go run main.go
```
or
```
# create an executable called go-tutorial
go build

# run the executable
./go-tutorial
```

What is the difference between the two methods to run your program? When we use `go run` the program is compiled and executed immediately. This translates the code into an executable that is deleted right after it is run. 
`go build` on the other hand is similar to the gcc. When we run `gcc main.c` for example an executable is created and in order to run this executable we must use `./a.out` to run the executable. Similarly, go build creates an
executable that is the name of the directory and `./go-tutorial` runs the executable.

| Command   | Description                                           |
|-----------|-------------------------------------------------------|
| `go run`  | Compiles and runs the Go program in one step.         |
| `go build`| Compiles the program and creates an executable file.  |

## Part 4. Push Your Changes to the Remote Repository
Remember the remote repository we created earlier? Let's push our changes to the remote so it's is updated.

1. Run the following commands in your terminal to move our changes to the remote repository:
```
git add .
git commit -m "Created our Hello Comp423 program"
git push origin main
```
