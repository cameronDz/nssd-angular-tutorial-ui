# Using Angular CLI to Create an Angular 9 web application #
Angular 9 is out, and with it a new version of Angular CLI. Creating a boiler plate application with Angular 9 continues to be incredibly simple and easy. This article will walk through how to create a basic application, and how to take advantage of the features included in a basic Angular 9 project.  

#### Overview ####
There are a few requirements you'll need on your machine if you want to follow this article and create the application. This is for users on Windows 10 machines, but since we are going to be using Git Bash, users on a Macs and Linux will be able to follow this guide as well. You'll need the following applications install; [NodeJS](https://nodejs.org/en/download/) (version 10.16), [Angular CLI](https://www.npmjs.com/package/@angular/cli) (version 9.0), [Git Bash](https://git-scm.com/downloads) (version 2.23), [Chrome](https://www.google.com/chrome/) (version 80.0), and [Visual Code](https://code.visualstudio.com/download). Each application is linked to an install page for Windows 10.


By the end, we will create and Angular applications using Angular's CLI (Command Line Interface), explore the features that Angular includes in it's boiler plate project, and go over some best practices. This article will not go over anything specific to Angular 9, but will be using the latest version of Angular at the time of writing.

#### Checking CLI Versions ####
In each of the CLI code segments throughout this article, the dollar sign (\$) will signify the start of a new command to be executed, and the double pound sign (##) will be a comment that is not part of the commands. Before you start, you should open a Git Bash terminal, then enter a few commands with some version flags. A flag, signified by a single or double dash after a main command, gives us a little more control in telling the command how to act, changing some default behavior of the command. These following commands will tell you if you are ready to start building your application.

```bash
$ npm --version    ## checks Node Package Manager installation
$ ng version       ## checks Angular CLI installation
$ git --version    ## checks Git installation
$ touch --version  ## checks Unix command installation
$ code --version   ## checks Visual Code installation
```

Each command will give you the install specs of the respective application. If you get a message that looks like; ```bash: <app-name>: command not found```, it means the application is not installed properly, or the install process wasn't finished. If that happens, use the links above to install/reinstall that program.

## Generating an Angular Application ##
Angular CLI makes it incredibly easy to create a new application. It sets all the configurations to build and run the application, as well as some additional features we'll go over. 


Just to cover the basics, Angular applications are written with Typescript. Typescript is written on top of JavaScript. You can actually write your entire Typescript file in pure JavaScript and it will work fine. Typescript adds functionality on top of JavaScript to help make code more reliable and resilient. 


Besides Typescript, since this is a web application, you'll also be using HTML (HyperText Markup Language) and CSS (Cascading Style Sheets). Now if you have all the applications listed installed, you are ready to start building your Angular application. 

#### Set up Project Directory ####
Once you verify that everything is installed correctly through the command line, let's move into the directory we plan on creating the project repository. I'll be creating mine in a new directory called project-repositories in my C drive. First open a Git Bash terminal, then run the following commands.

```bash
$ mkdir /c/project-repositories      ## create new directory
$ cd /c/project-repositories         ## move into directory
```

The first command makes the project-repositories directory, a directory to store application repository's on a local machine. The second moves the CLI into that as the working directory.

#### Angular's new Command ####
Now we will utilize Angular CLI to create a boiler plate (bare essentials) project. Run the following command.

```bash
## this will generate a basic Angular project
$ ng new md-angular-tutorial --prefix=md-tutorial --style=scss --skip-install=true --verbose=true
```

The main command, ng new md-angular-tutorial, is the Angular command to create a new boiler plate application structure, with md-angular-tutorial being the name of the new project and the root directory name. You should name the project something that suites you, but more than welcome to use the name I am using. I've also used four options flags with the command.


The first flag, prefix=md-tutorial, will set the default prefix prepended to all the components generated for our application. By default, this is set to app. You could use md-tutorial like I'm doing, or you could come up with something unique for your project.


The next flag, style=scss, sets the default style file type. Angular, by default, sets the style extension type to be CSS. Since SCSS(Sassy CSS) can use regular CSS syntax, as well as a lot of additional powerful features that can make styling more robust and easier to maintain in your application, and also make styling code look cleaner.


The flag, skip-install=true, will skip installing all the packages needed to run the application. Angular CLI can chug, take a little longer, when installing a project's packages. Because of this, we'll just use NPM (Node Package Manager), which will give us some time to go over the install process further.


The last flag, verbose=true, makes the logs in the CLI more informative. Sometimes, if a command is going to take several minutes to run, this can just confirm that the software is still running and hasn't frozen.

#### Opening the Project ####
After the ng new command finishes, you should get a message, "Successfully initialized git." Now in the Git Bash terminal, cd (command for Change Directory) into the new created project root, create a new git branch for developing our application changes, add some additional files the Angular project didn't generate, and open the project in Visual Code.

```bash
$ cd md-angular-tutorial/        ## move to project root
$ git status                     ## check repo branch/changes
$ git checkout -b project-setup  ## create new git branch
$ code -n .                      ## open Visual Code window
```

The first command, cd, moves use into the project root directory. Next, we check the branch and any changes in the repo (repository) using the git status command.


The git checkout command, is used to move between the different branches in you repository. Using the flag b will create the new branch and move you into that branch. This practice is good preparation for working on a group project where the work flow follows [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) as a source control framework.


The final command in this set, code, will open a Visual Code window. The n flag makes it a new instance of the application, in case you already have another project open. The period at the end is saying to open the current directory, since we are in the root of our project.

## Exploring a new Angular Application ##
Now that the project is setup up using Angular's ng new command, we can start exploring the different features, and what is built into the app to make development easier. Now we will install the application on our machine, and look at the npm run commands set up by default in the application by Angular.

#### Installing the Application ####
Since we skipped the initial install when we created the application, now is the time to do that. Use the following two commands in a Git Bash terminal.

```bash
$ npm install  ## download all required node modules for project
$ git status   ## check if repository has changes
```

The npm install command will give a good amount of terminal logs the first time it is run. This is information on the packages being used in the application. You may see deprecation warnings, security audit warnings, skipped dependency warnings, and information on how to support open source project you are using. When you run the git status command, you will see that there is a new un-tracked file, package-lock.json. So we will add the new lock file to source control with the following commands in Git Bash terminal.

```bash
$ git add .    ## add and stage package-lock file to source control
$ git commit -m "adding lock file"
```

The git add command will stage any file (tracked or un-tracked) in the path provided in the third argument to be added to git. Since we are you in the root of the project, we can use a period to say add any new file in the project to be staged.


The git commit command will save the changes that have been staged to the repository. The m flag lets us add a message afterwords, which will be the next argument. Even if it seems trivial, you should always put some basic commit message on every change you make.


The lock file is the only way you know when exact dependencies changed that are being used by Node when the project is build. So when something randomly breaks after you haven't made any changes besides a fresh install and build, you can see what changed in the lock file to try and track down a bug on an external project.


You should always commit the package-lock file to source control. What should never go into source control is the node_modules directory. This directory will contain thousands of sub-directories with tens of thousands of files that are not being maintained by your project, only used. By default, Angular adds that directory to the .gitignore file, which lists files that the repository ignores and doesn't track.


**Word of Caution**: You may run into merge conflicts in larger projects with the lock file. It's usually easiest to removed the changes completely from the branch causing the issues, merge the other changes, then do a fresh install, and commit the lock changes in a separate commit/pull request (PR). Pull requests are not standard in git, but on platforms like [BitBucket](https://bitbucket.org/), [GitHub](https://github.com/), and [GitLabs](https://gitlab.com/), pull requests are used as a way for developers to ask to put code changes into a repository, and easily view what changes will be made to the project. Pull requests are one of the easiest ways to do code reviews.

## Project Run Commands ##
Now that all the packages and node modules are installed and updated, we can take advantage of the npm run commands Angular has set up for the application by default.


All the npm run commands can be found in the package.json file. The scripts key in the file contains and object, and that object has several key names. Each key under scripts is a command. In the base Angular application, you'll have six basic commands. Here is what the scripts key looks like in a basic Angular application.

```javascript
"scripts": {
  "ng": "ng",
  "start": "ng serve",
  "build": "ng build",
  "test": "ng test",
  "lint": "ng lint",
  "e2e": "ng e2e"
},
```

Each command will run whatever is the value for the key. Here you can see that the npm run commands all call the Angular CLI command, ng. This means that if the machine attempting to run any of the commands doesn't have Angular CLI installed on it, all of the commands will fail.


Since we do have Angular CLI installed on our machine, let's look at the commands and what they do for the project.

#### Linting the Application ####
The first command we will look at is the npm run lint command. In the root of your project is a file named tslint.json. This sets rules for what is called a code linter; a low level code analyst tool that searches for style and coding errors. This can catch style errors like using double quotes over single quotes for string variables, or can catch someone using a single equal sign in an if statement rather than triple.

```javascript
if (someValue = someOtherValue) {
  // always executed because assigning value - linter will flag
}
if (someValue === someOtherVaalue) {
  // only executed when both values are equal
}
```

Its good to run the linter every once in a while to make sure your code stays clean and up to standards. You can lint the project with the following command in your Git Bash terminal.

```bash
$ npm run lint
```

Running this command on the initial project will show that all lint rules pass. Angular picked some standard rules most projects follow for Typescript linting. If you are interested in other rules that can be applied to your project, you can see the full list of rules on the [TS Lint GitHub](https://palantir.github.io/tslint/) page. There is also a VS Code plugin that you can install that will show anything that is flagged right in the IDE. It is called [TSLint](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin), published by Microsoft.


If you want to set best practices for styling like indentations, trailing white space, charset, etc., there is a file generated in the boiler plate project called .editorconfig. This file works with various plugins for different IDE's to set the style standards from the file. To take advantage of this in Visual Code, the most popular plugin now is [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig).


With the EditorConfig plugin installed on VS Code, every time you save a file in Code, all trailing white space will be removed. You can explore all the different rules you can set for IDE's to follow in the [EditorConfig](https://editorconfig.org/) homepage.

#### Running the Application's Unit Tests ####
Another great feature to the boiler plate project is the [Jasmine](https://jasmine.github.io/)/[Karma](https://karma-runner.github.io/) unit test configuration set up installed by default. Jasmine is the framework the tests are written in, which is also Typescript. Karma is the test runner, which creates the environment to run the tests. To see Karma run the default unit tests, in the terminal, enter the following command.

```bash
$ npm run test
```

Now, the project will be built, then a browser will open. Here you will see a list of all the test names with the number of passing tests. All test files are usually called spec files, with *.spec.ts extensions, hence why they are referred to as specs. Below the results of all the tests will be the Angular application.


What makes Karma really useful is, that while the tests are running, you can make changes to the code, and Karma will rebuild the project and refresh the test results. A good habit to get into is to leave a terminal open specifically for running the tests just to see if anything is breaks when you change code.


For now though, we can turn the tests off. Do this by selecting the terminal window, and pressing Ctrl +C to kill the process. After you do this, the Chrome window that was opened will close.


**Note**: If you try to close the Chrome window without terminating the process running the tests, the Window will reopen automatically.

#### Running the Application's End to End Tests ####
There is another framework Angular installs by default in the application, which is [Protractor](https://www.protractortest.org/#/). Protractor uses [Selenium](https://selenium.dev/) to run automated UI tests. These tests are a little more in depth, but they run similarly to the Jasmine/Karma tests; they will open a new Chrome browser instance and have each test. These tests only run once, so once they are done, the browser window will close and the terminal process ends. To run the tests, use the following command in the Git Bash terminal.

```bash
$ npm run e2e
```

Since these tests run so quickly, you won't be able to see the much. But the framework create the application and checked the the title was correct. This can be expanded to do things like click through lists, and enter text, and act as a real user would act. But for the testing actions like these, it requires significantly more effort than simple Jasmine/Karma tests.


**Note**: The e2e command requires Chrome version 80 in order to run. When I first ran the command, I was on 79, and got an error with the follwoing message embedded in the logs: "ChromeDriver only supports Chrome version 80". To update to the latest version of Chrome, open the browser, go to Settings in the menu tab, and select About Chrome. This page will show you the version you are running, and should give you the option to update if you don't have the latest.

#### Running the Application ####
Now that you know how to run the tests and linted your application, the only thing left to do is start the application with the npm run start command. While we've been using the Git Bash terminal for most commands up to this point, to start the application, we will take advantage of the terminal that VS Code provides. At the top of Code is a Terminal drop down. Click it, and choose New Terminal from the list. A new window will show up at the bottom of the IDE. To start the application, put the following command in the terminal.

```bash
$ npm run start
```

This will start up a [webpack server](https://webpack.js.org/configuration/dev-server/), which will run the application similarly to how Karma runs the Jasmine tests; every time you change the code, the application will be refreshed and show the code changes. The only difference is you have to manually open Chrome and go to the localhost port. By default, Angular sets the application to run on port 4200. Open Chrome and navigate to localhost:4200 to see your application running.


When you navigate to the application, you will see the application Angular set up. I would suggest exploring this page, and visiting the various pages it links to for other tutorials, documentation, and information on the frameworks Angular is using.


If you add the route, localhost:4200/webpack-dev-server, webpack will give you status reports on compilation errors and when the app is reloading/ready. It's also a good habit to get into to open the [Developer Tools](https://developers.google.com/web/tools/chrome-devtools) in Chrome by pressing Ctrl + Shift + I after opening the browser. You'll have access to the console to see logs you put in the code, as well as all the network traffic for API calls you make.


A convenient feature of the VS Code terminal is that you can also close the window within the IDE, and the application will still be running in the background. We can kill the application using the Garbage can icon in the panel, which is using the Kill the terminal and the process running.

## Modifying our Application ##
Now that we've seen the various features in the application, we can start to add and configure the application the way we desire.

#### Adding a Git Attributes Configuration ####
One of the advantages to have Git Bash installed on you machine, is that you have the option when install to get basic Linux commands installed in the terminal as well. We'll take advantage of this to generate our gitattributes file. In the Git Bash terminal, run the following command.

```bash
$ touch .gitattributes                 ## create git config file
```

Now, in VS Code, open the newly created file, .gitattributes. Take the code snippet below, and paste it into the file.

```
# set eol source control for file types
browerslist text eol=lf
.* text eol=lf
*.html text eol=lf
*.js text eol=lf
*.json text eol=lf
*.md text eol=lf
*.scss text eol=lf
*.ts text eol=lf
```

The configurations we added sets up how the EOL (End of Line) of a file type extension will be saved as in source control. Depending on what OS (Operating System) you are using, the EOL in a file is saved differently. Setting this configuration will help prevent issue when developing in different operating systems.


Since we will only be developing on a Windows 10 machine, we won't have this problem. This is more of a best practice to get in the habit of doing when creating new projects. Now let's save the file using the Save hot key, Ctrl + S. Then stage the file to be committed and commit the file using the following commands in Git Bash.

```bash
$ git add .gitattributes ## add specific file to source control
$ git commit -m "add git config for how eol should be saved"
```

#### Adding a Change Log ####
Another good practice to get into is to include a change log in your projects. Using Git Bash again, let's generate and add the change log to source control using the following commands.

```bash
$ touch CHANGELOG.md                    ## create change log file
$ git add CHANGELOG.md                  ## stage file
$ git commit -m "add empty change log"  ## give trivial message
```

A change log is used to track each release, and what goes into the project for each version. A good standard template for a change log comes from https://keepachangelog.com/en/1.0.0/. This change log follows the [SemVer](https://semver.org/spec/v2.0.0.html) versioning standards. This is the standard versioning format for most Node packages.


To start the change log for this project, open the newly created file in VS Code. Then, copy (Ctrl +C) and paste (Ctrl +V) the code block below to start the project change log (originally from the change log site above).

```md
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.0]
### Added
- Initial project commit.
```

If you plan on publishing a package or project for others to use and consume, a change log is the most straight forward way to tell users how your project has changed through each version. Commit the changes to the file with the following command.

```bash
$ git commit -am "update template for change log"
```

The am flag for the git commit command will stage any changes in files already in source control, and commit those files with the quoted message that follows.

#### Updating Package Details ####
We took a quick look at the package.json in order to see the various npm run commands. Now we will update to file with a little more information. Open the file in VS Code. We are going to add two keys to the JSON (JavaScript Object Notation); and author key and a repository key.


The author key is going to be an object, with two children keys; name and email. The repository key will also be an object, with two children keys, these being; type and url.


I will be using my own information for these keys. You should be using your own name/email in the author key. If you are going to put this project in GitHub or GitLabs, use that repository url key. If you will be keeping this project on your local machine, it can be an empty string.


These keys can go anywhere in the file, but for convience, we will put them at the top. To do this, copy and paste the code block below over the the first curly bracket in the package.json file of your project. Leave out the … as that just represents the file continues below.

```javascript
{
  "author": {
    "email": "camerondziurgot@gmail.com",
    "name": "Cam Dziurgot"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/cameronDz/md-angular-tutorial"
  },
...
```

 Save the added keys using Ctrl + S, then save the changes in source control through a Git Bash terminal using the following commands.

```bash
$ git status
$ git diff
$ git commit -am "add author/repo info to package"
```

The first command will just verify that only the package.json file has been changed. The next command, git diff, will show what changes are in the project that have not been staged yet. You will see the keys just added to the file. Finally the git commit command with the am flag will stage and commit the changed files.

#### Merging Back to Master ####
Since we've finished with installing and setting up the project configurations, we can now merge are branch back into the master branch.
We can do this by opening Git Bash, and running the follow set up commands.

```bash
$ git checkout master
$ git rev-list --count --left-right master...project-setup
$ git merge project-setup
```

The first command, git checkout, will put us into the master branch.


The next command has a little more content. The git rev-list command lists all the commits in chronological order. Putting the count flag on will output the number of commits. The left-right flag is used to compared commits between two branches, which is the next argument in the command in the following format: \<branch-a>…\<branch-b>. 


The full command we run will get the number of commits that each branch has that the other does not. The output from that command will be the following.

```
0       5
```

This output means that the master branch, \<branch-a>, has 0 commits that the project-setup branch, \<branch-b>, does not have, and the setup-project branch has 5 commits that the master branch does not have in its history. The reason we run this command is to show a way to compare branches through command line. This comes in handy when you are working in group projects and you want to check if your branch has fallen far behind the develop, or even master, branch. Here though, it's more just to demonstrate some of the features you can utilize with git.


The last command, git merge, will bring all the commits from the branch named in the next argument into the current branch. The output from that command will show all the files that were changed in the branch by the merge.

#### Tagging Version 0.0.0 ####
Now that we've merged all the changes we are going to make for tag for version 0.0.0. We can do this through Git Bash terminal and the following command.

```bash
$ git tag v0.0.0 -m "initial project setup version 0.0.0"
```

The git tag command will use the next argument as the tag name. The m flag will put a message for the tag, similar to commit messages.

## Conclusion ##
Now that you've generated the application and have some basic knowledge on the different tools Angular provides, it's time to explore the project on your own. All the content for the application is all located in the in a single HTML file, src/app/app.component.html file.


Let me know if this was helpful, and if you run into issues not explained in this article, feel free to post them to the [GitHub issues page](https://github.com/cameronDz/md-angular-tutorial/issues) for the repository I put this project.


Good luck and happy coding!


[Meduim Article](https://medium.com/@camerondziurgot/using-angular-cli-to-create-an-angular-9-web-application-aa1a5489dfdc) - Published 16 Feb 2020
