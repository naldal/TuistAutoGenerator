<p align="center" width="100%">
	<img width="575" alt="Logo" src="https://github.com/naldal/TuistAutoGen/assets/45508297/cd07e010-c205-4e08-a77b-ea248c45128d">
</p>

[🇰🇷 한국어로 읽기](https://github.com/naldal/TuistAutoGen/blob/main/README.Ko.md) |
[🇺🇸 Read in English](https://github.com/naldal/TuistAutoGen/blob/main/README.md)

<h3 align="center">🚀 A utility library for quickly building Tuist projects. </h3>

Welcome to TuistAutoGen. TuistAutoGen empowers you to fully control the Tuist project lifecycle with just one script execution.

**TuistAutoGen** is more than just another project creation tool. It's an enabler, a streamliner, a powerhouse that evolves alongside your project's needs. TuistAutoGen is an elegantly designed solution for swift project modularization and framework production, all just one shell execution away!

## Why use TuistAutoGen

Traditionally, creating a project using Tuist from scratch to finish poses several challenges:

**💀 Complexity** <br>
 Tuist, while powerful, is quite complex to set up and manage, especially for beginners. It involves various configuration files and requires understanding the Tuist DSL (Domain Specific Language) to create, manipulate, and manage projects.

**⏰ Time-Consuming** <br>
The process of setting up the project, managing dependencies, creating targets, and generating the Xcode project can be time-consuming, particularly for larger projects with multiple modules and dependencies.

**🧟 Prone to Human Error** <br>
The manual process of configuration and setup can lead to human errors, resulting in broken builds or runtime issues.

**😓 Difficulty in Modularization** <br>
While Tuist supports modularization, setting up a modular project can be challenging and involves numerous steps. This includes creating separate modules, managing interdependencies, and ensuring each module can be built independently.

**🦿 Framework Generation** <br>
Generating frameworks for a project involves a significant amount of manual work, including setting up the targets, linking dependencies, and managing build settings.

These inherent difficulties often result in slowed down development speed, increased bug risks, and a steeper learning curve for developers new to the system.

On the other hand, **TuistAutoGen** drastically simplifies these steps by automating project creation, modularization, and framework generation, thus eliminating the aforementioned hurdles. It makes using Tuist a breeze and significantly accelerates the project setup process, reduces the potential for human error, and makes managing complex, modularized projects simple and straightforward. This highlights the advantages of TuistAutoGen and makes it an essential tool for every iOS developer.

## Usage

### Required installations
TuistAutoGen is written based on Tuist version 3.11.0.
Please stick to this version for TuistAutoGen to work properly.

However, if you don't have any installed on your Mac, you may need Homebrew or utility software such as mise, curl, etc.

I've created and distributed another shell script file called TuistInstaller to solve this problem a little more elegantly.
[TuistInstaller here](https://github.com/naldal/TuistInstaller/tree/master)

TuistInstaller provides the necessary elements for installing Tuist.

### Basic Usage
> **Note:** TuistAutoGen is based on bash 5.2.15 RC version (aarch64-apple-darwin22.1.0)
> Too low of a Bash version can interfere with the functioning of the shell script.

To make a single Application, just type command below on your **bash shell**. 
```bash
./autoGenerator.sh --main $projectName
```
For example,
```bash
./autoGenerator.sh --main CoreProject
```
The project name you set will be the main project's name!

Next, we generate the project's name.
```bash
🏃 Start to generate Tuist Projects!
✍️ What is the name of new Project?
✏️ Your Name of Project is :
<Setting Project Name>
```
The chosen name will become the name of the entire project!

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **Project** <br>
&nbsp;&nbsp;┗ 📂 **Main Application**

Now, the Main project that you set is generated on the under the Project
Go to **TuistProject** to generate your project.
```bash
cd TuistProject
```

and run the Tuist generate
```bash
tuist generate
```

..and you are done! 
The Basic Application will be generated 🎉

## "Main" Project Structure

🖐️ Before we proceed, it is necessary to understand the structure of the main project we have created. Let's examine the accompanying image that explains the organization of **The Main Project structure**.

<p align="center" width="100%">
<img width="967" alt="mainProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/592389f8-cadb-4be8-b876-b2bf90ee39f2">
</p>

There are two folders in the main project: **Supports** and **Target**.
- The **Support folder** contains the **InfoPlist** and **BridgingHeader** folders. Each folder serves a specific purpose:
  - The _InfoPlist folder_ holds the Info.plist file, which can include various types of information as needed.
  - The _BridgingHeader folder_ contains a header file that facilitates interaction between Swift and Objective-C.
- The **Target folder** comprises the _Resources_, _Sources_, _Tests_, _TestResources_, and _XCConfigs_ folders.
	- The _Resources folder_ manages the application's assets, such as images, colors, and localizable strings. TuistAutoGen automatically generates Image.xcassets and Color.xcassets catalogs within this folder.
	- The _Sources folder_ is where you can freely code your own logic.
	- The _Tests folder_ is designated for unit tests. TuistAutoGen strongly recommends performing tests and automatically includes the Test Library Quick and Nimble.
	- The _TestResources folder_ is where you can store resources specifically for testing purposes.
	- The _XCConfigs folder_ is used to manage any custom Xcode configuration files.

## Understanding Options

TuistAutoGen has four input options: main, includeOnly, include, and framework. Each option determines the type of project to be generated during project creation.

|input Options   |Explaination
|----------------|-------------------------------
`--main`         |a Main Application             
`--includeOnly`  |an Application base on Main Application            
`--include`      |an Application base on Main Application and also have own Sources and Resources
`--framework`    |a Framework


### Usage with Options
**Now, you can use variety cases with these options!**

Case 1) Let's assume that you want to create a main application and an includeOnly application.

```bash
./autoGenerator.sh --main $Main_ProjectName --includeOnly $Include_Only_ProjectName
```

The following folder structure will be created.

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **Project** <br>
&nbsp;&nbsp;┗ 📂 **Main Application** <br>
&nbsp;&nbsp;┗ 📂 **IncludeOnly Application**<br>

<br>

Case 2) Let's create two includeOnly applications and one include application.

There is no problem at all. 😎
```bash
./autoGenerator.sh --main $Main_ProjectName --includeOnly $Include_Only_ProjectName_One --includeOnly $Include_Only_ProjectName_Two --include $Include_ProjectName
```

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **Project** <br>
&nbsp;&nbsp;┗ 📂 **Main Application** <br> 
&nbsp;&nbsp;┗ 📂 **IncludeOnly Application 1** <br>
&nbsp;&nbsp;┗ 📂 **IncludeOnly Application 2** <br>

<br>
Case 3) What about generating a framework?

```bash
./autoGenerator.sh --main $Main_ProjectName --framework $Framework_ProjectName
```

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **Project** <br>
&nbsp;&nbsp;┗ 📂 **Framework** <br>
<br>

Now, let's explore what these options mean, their structure, and why they are necessary.


## "IncludeOnly" Project Structure
The `--includeOnly` option provides a unique approach for project organization. It allows for the creation of a project structure that includes all folders from the Main project while keeping the "includeOnly" project itself devoid of sources and resources.
<p align="center" width="100%">
<img width="958" alt="includeOnlyProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/cc643f40-6d02-4bd9-9a20-32fcee5881e8">
</p>


### Why is the `--includeOnly` option needed? 
The necessity for the `--includeOnly` option arises from its capacity to promote a cleaner, more organized project structure. It provides a way to include necessary components from the Main project without crowding the "includeOnly" project with additional resources or source files. This can be particularly useful for large-scale projects where different components need to reference shared resources, or when maintaining a lean project structure is of paramount importance. The `--includeOnly` option simplifies navigation and management, and ensures a more streamlined project setup and maintenance process.

Consider the scenario where you're developing an application that has multiple variants - let's say, a "Dev" and a "Prod" version. Both versions share the same base structure and many resources, but the "Dev" version might include extra debugging tools, test data, or configuration settings.

In this case, the `--includeOnly` option can be a powerful tool. Here's how it might work:

Your Main project includes all the source code and resources shared across both the "Dev" and "Prod" versions. This project forms the backbone of your application.

Next, you create an "includeOnly" project specifically for the "Dev" version. Using the `--includeOnly` option, this project will include all the folders from the Main project but won't have its own sources or resources. Instead, it could contain specific debugging tools, additional configuration settings, or even test data exclusive for the development environment.

This setup allows you to easily switch between the "Dev" and "Prod" versions while keeping your project structure clean and organized. Each version has its own dedicated project but shares the same base structure and resources, ensuring consistency while allowing for version-specific customization.


## "Include" Project Structure
The `--include` option presents an effective method for project organization and resource allocation. When used, it instructs the include project to encompass all folders from the Main project while maintaining its unique sources and resources.
<p align="center" width="100%">
<img width="966" alt="includeProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/1992021f-958f-45ed-819a-aaaed7129d03">
</p>

### Why is the `--include` option needed?
The need for the `--include` option stems from its ability to promote a flexible, adaptive project structure. It facilitates the process of incorporating necessary components from the Main project, while allowing the include project to retain its individual resources and source files. This can prove highly beneficial for situations where different components of a project need to reference shared resources while still maintaining their own unique files.

For instance, imagine you are working on a project with multiple modules that share a common structure and resources but also require their own specific functionalities. Using the `--include` option allows you to preserve this shared structure from the Main project while each module retains its unique capabilities.

The `--include` option ensures that while the core structure remains consistent, there's room for individuality and customization where it's needed. It simplifies project navigation, management, and provides a more efficient workflow for developers.

## "Framework" Project Structure
The `--framework` option signifies the creation of a project intended to be a framework. This framework will maintain its unique Resources, Sources, and include a sample application.

<p align="center" width="100%">
<img width="977" alt="스크린샷 2023-06-15 오후 4 43 10" src="https://github.com/naldal/TuistAutoGen/assets/45508297/6bf25d0b-85d3-4be9-a0d8-dbe92699ab0d">
</p>

### Why is the `--framework` option needed?
The necessity for a framework stems from its ability to encapsulate code into reusable, independent components. By using the `--framework` option, developers can organize code in a way that promotes reusability, reduces complexity, and improves code maintainability. A framework can contain its specific Resources and Sources, allowing for a self-contained package of functionality that can be easily shared across multiple projects or applications.

For instance, imagine having a set of functionalities or services, such as networking or database management, that are used across different projects. By bundling these functionalities into a framework using the `--framework` option, you can reduce code redundancy, streamline your development process, and increase the overall reliability of your code.

Moreover, a framework also comes with a sample application. This aids in testing the framework's functionality and serves as a practical example for developers to understand how to integrate and use the framework within their own projects.

In summary, the `--framework` option plays a crucial role in creating a modular, organized, and maintainable codebase, which is a key aspect of modern software development methodologies.


## Concluding
With this, you are now primed to construct Tuist projects effortlessly using the powerful tool, TuistAutoGen.

As we reach the conclusion of this documentation, we invite you to explore the remarkable capabilities of TuistAutoGen. Utilize it as your catalyst to streamline the project creation process, bolstering your productivity and fostering an efficient development environment. Dive in, experiment, and discover the ease and efficiency TuistAutoGen brings to your Tuist projects. The future of effortless project creation is at your fingertips with TuistAutoGen. Enjoy your journey!

## 🗺️ Road Map

 * [x] 📦 enabled to generate just only framework
 * [ ] 🫥 adjust auto codesign
 * [ ] 🖌️ adjust tuist stencil


## ⚖️  License
The MIT License (MIT)

Copyright (c) 2023 Hamin Song

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
