# Setting up a dev container for Go

* Primary author: [Ayush Godhani](https://github.com/avgod07)
* Reviewer: [Prasun Sapkota](https://github.com/psap2)

Hello! In this tutorial we will learn how to set up a dev container for Go. By the end of this tutorial you will have created a Go Development Container in VS Code, making development much easier.

## Prerequisites
1. A GitHub account: If you don’t have one yet, sign up at [GitHub](https://github.com).
1. Git installed: [Install Git](https://git-scm.com) if you don’t already have it.
1. Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com).
1. Docker installed: Required to run the dev container. [Get Docker here](https://www.docker.com).

## Part 1: Project Setup: Creating a Repository

### Step 1. Crerate a Local Directory and Initialize Git

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
   echo "# Setting Up a Project with Go"
   git add README.md
   git commit -m "Initial commit with README"
   ```

### Step 2. Create a Remote Repository in Github
1. Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.
1. Fill in the details as follows:
   * **Repository Name**: `comp423-course-notes`
   * **Description**: "Course notes organized as a static website using Material for MkDocs."
   * **Visibility**: Public
1. Do not initialize the repository with a README, .gitignore, or license.
1. Click **Create Repository**

### Step 3. Link your Local Repository to GitHub
1. Add the GitHub repository as a remote:
   ```
   git remote add origin https://github.com/<your-username>/comp423-course-notes.git
   ```
Replae `<your-username>` with your GitHub username.
1. Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.
1. Push your local commits to the GitHub repository:
   ```
   git push --set-upstream origin main
   ```
1. Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use `git log` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

## Part 2. Setting Up the Development Environment

### Step 1. Add Development Container Configuration
1. In VS Code, open the `go-tutorial` directory. You can do this via: File > Open Folder.
1. Install the Dev Containers extension for VS Code.
1. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

   `devcontainer/devcontainer.json`

   The `devcontainer.json` file defines the configuration for your development environment. Here, we're specifying the following:
  
   * `name`: A descriptive name for your dev container.
   * `image`: The Docker image to use, in this case, the latest version of a Python environment. [Microsoft maintains a collection of base images for many programming language environments](https://hub.docker.com/r/microsoft/vscode-devcontainers), but you can also create your own!