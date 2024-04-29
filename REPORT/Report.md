# Building a CI/CD Pipeline for a Flutter Application
## Introduction
**Continuous Integration/Continuous Deployment (CI/CD) pipelines** are integral parts of modern software development. CI is the practice of frequently integrating code 
changes into a shared repository. With each code change, automated builds and tests are triggered to detect any integration issues early in the development process. 
CI ensures that the latest code changes from multiple developers on a project are merged and tested continuously. CD is the practice of automating the deployment process
to release code changes into production environments frequently and with reliability. CD pipelines automate various stages of the deployment process, including building, testing, and deploying applications to different environments (e.g., development, staging, production).
CD enables teams to deliver new features, fixes, and updates to end-users quickly and efficiently.


**Significance**
- **Improved Code quality:** CI/CD pipelines automate code testing and validation, leading to higher code quality.
- **Faster time to market:** CI/CD pipelines enable faster delivery of software updates, features, and bug fixes to users, reducing time to market.
- **Increased Collaboration:** CI encourages collaboration among team members by continuously integrating code changes into a shared repository, facilitating early feedback and collaboration.
- **Scalability:** CI/CD pipelines are scalable and adaptable to different project sizes and complexities. They can handle large codebases and complex deployment scenarios efficiently.

## DevContainer Environment
The base image used was the docker image built for flutter development. This image includes the flutter SDK, dart, and other essential tools. The devcontainer.json file was modified to contain "postCreateCommand": "sudo chown -R vscode /flutter/.pub-cache"
This project was completed using vscode so the devcontainer enviornment was made on there.

**DevContainer features**
- **"image": "mcr.microsoft.com/devcontainers/base:jammy":** This specifies the Docker image to use for the development container. The jammy image used contains a base Ubuntu image configured for development purposes.
- **"features": { "ghcr.io/jarrodcolburn/features/flutter-sdk:0": {} }:** This specifies additional features or extensions to include in the development container. Here, the feature ghcr.io/jarrodcolburn/features/flutter-sdk:0 was added. It contains the Flutter SDK and associated tools for Flutter development.
- **"postCreateCommand": "sudo chown -R vscode /flutter/.pub-cache":** This specifies a command to run after the container is created. In this case, it runs sudo chown -R vscode /flutter/.pub-cache.
  - sudo: Executes the command with root privileges.
  - chown: Changes the ownership of files and directories.
  - R: Recursively changes ownership for all files and subdirectories.
  - vscode: Specifies the user to change ownership to. This is the user running Visual Studio Code in the development container.
  - /flutter/.pub-cache: Specifies the directory to change ownership for. This directory is used by Flutter for caching packages.

## Source Code Version Control Tools
**Description:** This project utilized Git as its version control system. There are many benefits to using Git, as it is a very powerful and commonly used version control system. 
To begin with, Git allows every developer working on the project to have a complete copy of the repository and it's full history. Git also has merging and 
branching capabilities that allow developers to easily create branches to work on new features or fixes without affecting the main codebase. Merging these changes 
after working on them in another branch minimizes the risk of conflicts. Another benefit of Git is its speed and efficiency. The process of committing, branching, 
and merging is typically fast and doesn't slow down the development process. Overall, Git was chosen as the version control system for this project because of 
its efficiency, way of organization, vast ecosystem of tools, plugins, and integrations, and because of how commonly used it is among software developers.

**Integration with CI/CD:** Git plays a crucial role in CI/CD pipelines by providing the source code repository where changes are pushed. In CI, many of the changes
made are merged into the repository from various branches, triggering automated builds and tests. Thus, CI tools monitor the git repository for new changes and 
automatically trigger build and test jobs when new commits are pushed. These CI jobs fetch the latest code from the Git repository, build the application, run tests, 
and provide feedback on the code quality and test results. From this, we receive immediate feedback on the status of their changes, enabling us to address issues early in the development cycle.
In CD, automated deployment pipelines deliver code changes to production or staging environments. Git was used to manage deployment configurations and track changes to deployment scripts.
CD pipelines are typically triggered after successful CI builds, ensuring that only validated code changes are deployed.
CD tools integrate with Git repositories to fetch the latest code and execute deployment steps. These pipelines automate tasks such as building Docker images, deploying containers, updating server configurations, and orchestrating deployments.
Git branches and tags can be used to control which versions of the code are deployed to specific environments, allowing for controlled release processes.


## CI/CD Pipeline Environment:
The configuration used in this project describes a CI/CD pipeline named "Main Pipeline" that automates the build, test, and deployment process for the Flutter web application. Here is a breakdown of the setup:

**Pipeline Configuration:**
1. Trigger:
    - The pipeline is triggered on push events to the main branch of the repository.
2. Jobs:
    - The pipeline defines a single job named "Pipeline" that runs on an Ubuntu environment (ubuntu-latest).

**Steps:**
1. Checkout:
    - The pipeline first checks out the source code of the repository using the actions/checkout action.

2. Flutter Setup:
    - The pipeline uses the subosito/flutter-action action to set up Flutter with the specified channel (stable).
  
3. Install Dependencies:
    - It installs dependencies for the Flutter web application by running flutter pub get in the ./app directory.

4. Run Tests:
    - It runs tests for the Flutter web application using the flutter test command in the ./app directory.

5. Build Flutter Web:
    - It builds the Flutter web application using the flutter build web command in the ./app directory.

6. Deploy:
    - Finally, it deploys the built web application to GitHub Pages using the peaceiris/actions-gh-pages action.
    - It uses the GitHub token (${{secrets.GITHUB_TOKEN}}) to authenticate with GitHub.
    - The publish_dir option specifies the directory containing the built web files (./app/build/web).
  
**Environment:**
- The pipeline runs on GitHub Actions, a CI/CD platform provided by GitHub.
- It utilizes the ubuntu-latest environment for running the jobs.
- The Flutter web application is built and tested within the CI/CD environment.

**Cloud Services:** 
- GitHub Actions is used as the CI/CD platform to automate the pipeline workflow.
- GitHub Pages is used as the hosting service to deploy the built Flutter web application.

## CI/CD Tools
**GitHub Actions:**
1. Configuration:
     - Workflows are defined in YAML files (Main.yml) within the .github/workflows directory of the repository.
    - Actions are triggered by events such as pushes, pull requests, or scheduled tasks.
    - Workflows consist of jobs, which run sequentially or concurrently, and each job contains steps to execute commands.
2. Roles
    - **Automation:** GitHub Actions automates the entire CI/CD workflow, including building, testing, and deployment.
    - **Integration:** It integrates seamlessly with GitHub repositories, allowing us to define and manage workflows directly within our projects.
    - **Flexibility:** GitHub Actions offers a wide range of pre-built actions and supports custom actions, enabling us to tailor workflows to our needed requirements.
    - **Scalability:** It automatically scales to handle large workloads and parallel executions of workflows.

  ## Deployment Environment

**GitHub Pages:**
1. Overview: 
    - GitHub Pages is a static site hosting service provided by GitHub.
    - It allows us to host our Flutter web application directly from a GitHub repository.
2. Setup Configurations:
    - We first built our Flutter web application
    - We then created a gh-pages branch in the GitHub repository.
    - Next, we pushed the contents of the build/web directory to the gh-pages branch.
    - Finally, we had to go enable GitHub Pages in the repository settings and specify the Main branch as the source.

## Flutter Web Application:

**Functionality:** The flutter web application for this project is the default one. It includes a basic UI with a counter widget and a button to increment the counter.
When the button is clicked, the number of times the button has been clicked goes up by 1. 

**Testing:** Flutter test was used in this project to do a lot of the testing. These are automated tests written using the Flutter testing framework to verify the behavior and functionality of specific components, widgets, or classes within the application. They provide more granular testing and can cover individual units of code, UI components, or integration scenarios.

**Deployment:** There were many challenges with deployment for this application. At first, we were not able to get the app to deploy to GH-Pages, however, this was fixed by going to settings and changing the configurations of GH-Pages there. 

## Conclusion
**Challenges Encountered:**

Deployment Issues: We faced difficulties deploying our Flutter web application, possibly due to misconfigurations, dependencies, or compatibility issues. These challenges highlighted the importance of thorough testing and validation before deployment.

Environment Setup: Setting up the CI/CD environment and ensuring compatibility with Flutter web applications was very challenging, especially because we were new to CI/CD and Flutter development.

Testing Complexity: Managing and writing tests for a Flutter web application, particularly integration tests that involve multiple components or external dependencies, presented challenges in terms of complexity and maintenance.

**Potential Improvements:**
Refinement of CI/CD Pipeline: With more knowledge on the pipeline, we can revisit the configuration, adding additional tests or checks, or improving error handling mechanisms.

Enhanced Testing Strategy: We could also evaluate our testing strategy and consider incorporating more comprehensive testing practices, such as end-to-end testing or performance testing, to ensure the robustness of the application.

Overall, this project was very informative on the many benefits of using a CI/CD Pipeline. While it was very challenging, exploring the benefits of a CI/CD 
pipeline in this project has been highly informative, showcasing its pivotal role in modern software development. CI/CD pipelines make building, testing, and deploying much more efficient, especially in collaborative spaces. This is important, as comprehensd collaboration among team members 
ensure consistency and facilitate knowledge sharing. I am looking forward to learning more about the CI/CD Pipeline and implementing it into my career in this field.
