## DevContainer Environment 
## Introduction
A development container is a self-contained and portable enviornment used for software development. It encapsulates all the necessary tools, dependencies, and configurations required for a project. DevContainers
ensure consistency and reproductibility in environments across different devices and platforms. It eliminates the "it works on my machine" problem, which can lead to compatibility issues and bugs. In the context of 
a flutter app development, devcontainers offer the following benefits: It makes a much more consistent flutter environment, which is important because flutter apps often rely on specific versions of flutter sdk, 
dart language, and dependencies. By using a devcontainer, the flutter app will also have its own controlled and isolated environment, which prevents conflicts with other installed software or libraries. Having a 
flutter devcontainer also reduces time that could otherwise be spent setting up development environments. 

## Configuration 
The base image I used was the docker image built for flutter development. This image includes the flutter SDK, dart, and other essential tools. I also adjusted the devcontainer.json file to contain 
"postCreateCommand": "sudo chown -R vscode /flutter/.pub-cache". For my project, I am using vscode so I made my enviornment on there.

## Integration with VS Code
VS Code allows users to define a development environment for their project using docker containers. The heart of the devcontainer integration is in the .devcontainer folder in the project. Within this folder,
the devcontainer.json file defines the container configuration, including base image, and other extensions that can be added in. VS Code allows developers to execute commands within the container directly from the
VS Code terminal. 

## Usage
In order to make and start a container, open the file in which you will make your container. Next, open a remote window in the left corner. Click add devcontainer configuration files and then add configuration to 
workspace. Then select the following, Ubuntu->Jammy->Flutter->keep defaults. Once you reopen the container, add any additional dependencies or extensions needed in the devcontainer.json file. For mine, I added the 
postcreatecommand. After this, rebuild the container. In order to make a new flutter application, you can type "flutter create appName" in the terminal. The app can be run by using the flutter run command. You can
also run the command "flutter pub get" in order to install or update any dependencies defined in your pubspec.yaml file. If you want to close the container, you can simply close the remote connection. By following
these steps, you can integrate devcontainer in your development workflow. 

## Challenges and Solutions
The main challenge I encountered with setting up my devcontainer was figuring out how to create the container itself. I had a difficult time navigating VS Code and understanding docker files. I learnt and better 
understood how to make a containerized environment with practice and by playing around with VS Code a bit.

## Conclusion
The overall benefits of using the devcontainer for this project is to learn how to make a consistent environment in order to create a more productive and stable working environment. Using devcontainers is also 
really good for reproducibility as it makes it easy to reproduce the development environment across different machines, ensures consistent builds, and makes debugging easier. It also allows for easy sharing and
collaboration of the project. I never considered the importance of the development environment of a project until beginning this process. 



