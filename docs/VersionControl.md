# Source Code Version Control Tools

## Introduction

Version control is an aspect of software development that facilitates the management of code changes throughout the development process. 

- **Integrity:** Version control ensures the integrity of a codebase by keeping track of changes made by different developers over time. It allows developers to revert back to previous changes if new changes bring about bugs or issues, thus reducing the risk of code conflicts and maintaining a more stable codebase.   
- **History:** Version control systems maintain the history of all changes made to a codebase, which is valuable for understanding the evolution of the project and diagnosing issues. We can see who made the changes, when they were made, and what changes were made.  
- **Collaboration:** Version control facilitates collaboration among team members by providing mechanisms for seamless sharing and synchronization of code. Developers can branch off and work on different aspects of the project simultaneously. Changes made by different developers can be merged into the main codebase.

## Version Control System Used

This project will be using Git as its version control system. There are many benefits to using Git, as it is a very powerful and commonly used version control system. To begin with, Git allows every developer working on the project to have a complete copy of the repository and it's full history. Git also has merging and branching capabilities that allow developers to easily create branches to work on new features or fixes without affecting the main codebase. Merging these changes after working on them in another branch minimizes the risk of conflicts. Another benefit of Git is its speed and efficiency. The process of committing, branching, and merging is typically fast and doesn't slow down the development process. Overall, Git has been chosen as the version control system for this project because of its efficiency, way of organization, vast ecosystem of tools, plugins, and integrations, and because we already have a bit of familiarity with it, seeing as it is very commonly used. 

## Repository Setup

- **Structure of the repository**
  - **Branching Strategy**: The main branch will be used for the main aspect of the codebase. Other branches may be developed for future commits and merges 
  - **Directory Layout**: This repository is organized with the following directories:
    - The .devcontainer directory containing the devcontainer.json file, which defines the container environment
    - The .github directory containing a workflows directory, which contain build.yml and deploy.yml
    - The app directory containing the source code for the project
    - The docs directory which contains documentations such as this one and DevContainer.md. These documents outline sections of the CI/CD pipeline 
- **Integration with DevContainer and CI/CD Pipeline**: DevContainer provides a consistent development environment for all collaborators on the project. The devcontainer is stored within the repository, allowing developers to easily set up their development environment. The CI/CD pipeline is responsible for automating various stages of the process such as building, testing, and deploying the application. The pipeline is integrated with the repository, triggering automated processes in responses to code changes made. We use build.yml to define the building process of the project, such as compiling source code, running tests, and packaging artifacts. We use deploy.yml to define the deployment process, which contains instructions for how to deploy a project to a target environment.
- **Standards and Conventions Adopted**: We use conventional commit message formats, consistent branch naming conventions, and adhere to coding standards. See [adopted standards and conventions](https://dev.to/varbsan/a-simplified-convention-for-naming-branches-and-commits-in-git-il4) here.

## Common Commands and Usage

- `git commit -m "Commit message"`: Commits changes to the local repository. This will be used to detail any changes being committed in the project.
- `git merge <branch>`: Merges changes from the specified branch into the current branch. Changes made in other branches may need to be merged into the main branch for the project.
- `git log`: Displays commit history. This will be used when the history of the repository needs to be viewed. It may come in handy to review changes, track down bugs, and more
- `git revert <commit>`: Reverts changes introduced by a specific commit. This will be useful for undoing changes made in previous commits without changing the commit history.
- `git add .`: Stages all changes in the current directories and its subdirectories for the next commit
- `git branch`: Shows a list of all the branchs in the repository. An asterisk (*) is placed next to the branch that is currently checked out.
- `git checkout <branch>`: Switches out of the current working branch into the branch mentioned in the command

## Collaboration Features

Git facilitates collaboration through pull requests, code reviews, and conflict resolution mechanisms.   
- **Issues:** Developers can create issues and assign them to other team members, furthering collaboration on a project.
- **Pull requests:**: Git allows developers to work in their own branches. Once a developer completes work in a branch, they can push their branch to the remote repository and create a pull request. Pull requests bring team members together for collaboration, as developers can review the changes, ask questions, and provide feedback on the proposed modifications.
- **Collaborative conflict resolution:** Git facilitates collaborative conflict resolution by enabling developers to communicate and coordinate efforts during conflict resolution. Team members can discuss the conflicting changes, decide on the appropriate resolution strategy, and ensure that the final merge preserves the integrity of the codebase

## Challenges and Solutions
The challenges faced using git for this project mainly revolve around using git commands/features and navigating the project repository. Some challenges and their solutions can be found [here](https://www.gitkraken.com/learn/git/problems).

## Conclusion

Using git as the version control system for this project has many benefits. Git allows for effective collaboration among developers, is very efficient with history tracking , as it maintains records of all changes made to the codebase, helps maintain the integrity of the codebase by tracking changes and providing mechanisms for reverting to previous versions if needed, and more. Integrating git with the devcontainer and CI/CD pipeline helps automate various aspects of the development workflow, such as environment setup, testing, and deployment. 
