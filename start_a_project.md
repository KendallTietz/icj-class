# How to start a project

A cheatsheet and lesson on how to start a new project from scratch for Intro to Coding for Journalists. Students may use this in the early weeks of the class to create projects.

Starting a new project with `degit`, which we use later in the semester, is at the [bottom](#using-degit).

## Overview of the steps

These are the overall steps in case you just need reminders of the order. A more detailed breakdown is [below](#a-very-detailed-version-of-starting-a-new-project).

- Create a new folder for your project inside your `icj` folder. (You can use your regular computer operating system to do this.)
- Launch VS Code.
- Use **File > New Window** to open a fresh window.
- Use **Open folder** to then find and choose your new folder.
- Create a `README.md` file.
  - Using [Markdown](#create-your-README), add a headline with the project name. Add text with your name and the due date of the project.
  - Save the file.
- Create a `.gitignore` file.
  - Use [gitignore.io](https://www.gitignore.io/) to create the contents of your gitignore file. Use the values "macOS", "Windows" and "VisualStudioCode" and Create. Copy the contents into the file you created.
  - Save the file.
- Commit your local files. In your Terminal do the following:
  - `git init` to initialize git.
  - `git add .` to add all the files to stage.
  - `git commit -m "initial commit"` to commit the files.
- Go to Github.com and add a **New Repository**.
  - Name it the same as your local folder.
  - DO NOT include the README or .gitignore files.
- Once created, review the lines of code Github suggests:
  - Find the line that starts `git remote add origin` and copy that line.
- Back in VS Code:
  - Enter that copied line in your Terminal and run it.
- Do `git push origin master` to push you local code to Github.

You are now ready to complete the rest of the assignment. You can use the git cycle to commit any further changes.

## The git cycle

As you work through the project, use the git cycle to save your code to your local machine, then push those changs to Github.

- `git status` tells you where you are in the it cycle.
- `git add .` adds all changed files into your stage
- `git commit -m "Your message"` commits your changes to your computer.
- `git push origin master` pushes your local changes to Github.

## A very detailed version of starting a new project

This is the same as above, but with more detail, description and visuals.

### Create your project folder

I find it easiest to create the folder using your computer's operating system: [macOS](https://support.apple.com/guide/mac-help/organize-files-using-folders-mh26885/mac) | [Windows](https://www.laptopmag.com/articles/create-new-folder-windows-10).

Create this folder inside you `Documents/icj` so you always know where your code is for this class.

- The assignment will guide you on how to name the folder.
- Always start the folder name with your own name.
- Use all lowercase letters. It's just helpful.
- Use dashes instead of spaces in the name. It's helpful, and depending on the project the folder name can end up being part of a URL.

An example:

`christian-project-name`

### Open the folder in VS Code

Opening the folder in VS Code will make sure that your computer knows where all the files are relative to that folder.

- Launch VS Code
- You might close any windows that might still be open.
- Choose **File > New Window**.
  - If your document tray is open, you might see a big button for **Open Folder**. Click it.
  - Or, you can go to **File > Open** (Or use the keyboard command: _Command-O_).
- Once the folder opens, the document tray should show the folder name.

![Folder name](images/00-folder-open.png)

### Create your README

Here is a reminder of [why we make a README file](https://www.makeareadme.com/).

I find the easiest way to create a new file is to use the Terminal. There are many other ways, but `touch` is the best all-around way.

- If your Terminal isn't open already, go to **Terminal > New Terminal**.
- Do `touch README.md`

This will create the file and you'll see it in the Document tray.

For this class, I want to to at least include this information in your README, adjusted based on the project, of course.

```md

# The project name

By Christian McDonald

The project is due on Month Day Year.
```

### Create the .gitignore file

The `.gitigore` tells git to ignore certain files your computer will create but don't need to be committed to the repository.

- `touch .gitignore` will create the file.
- In a browser, go to [gitignore.io](https://gitignore.io)
- Insert the following values

![gitignore values](images/00-gitignore-values.png)

- Hit **Create**
- Copy all the text from the resulting window.
- Paste it into your `.gitignore` file in VS Code. Save the file.

### Commit your local files

It's now time to use the parts of the git cycle to commit your files to your local machine, but first we have to tell git that we want to by initializing it.

- `git init` to initialize the project.
- `git add .` to add all the files to stage.
- `git commit -m "First commit"` to save the files.

We have to create and connect to Github before we can push them.

### Create your Github repo

Now we create the repo in Github so we can connect to it.

- Go to [Github.com](https://github.com) in a browser and log in if you aren't already.
- At the top right of the page is a big **+** sign. Click on that and choose **New repository**.
- For the repository name, I recommend you use the same name as you used for your local folder. Like `christian-project-name`.
- The **Description** is optional.
- Keep it **Public**.
- DO NOT use the README or gitignore options.
- Click the **Create repository** button.

Once you create the repo, you'll get a page back with a lot of code.

- Make sure the `SSH` button is selected in the top box.
- Look for the line that starts with `git remote add origin` and copy that line.

![Connect to Github](images/00-connect-github.png)

- Go back to VS Code and paste the command into your Terminal and run it.
- `git push origin master` will then push your changes to Github.

If you want to make sure it worked, go back to your browser and refresh the page and you should see your files there.

You should now be ready to continue with the assignment.

## Using degit

Some projects we do in the class begin with a set of template files that already include a README and gitignore file.

- Create your project folder inside the `icj` folder.
- Launch VS Code and open the folder.
- `degit utdata/template-name` will download all the files into your folder. BUT YOU'LL WANT TO USE THE CORRECT TEMPLATE NAME.
- `git init` will initialize the repo
- `git add .` to add the files
- `git commit -m "first commit` to save the files.
- Create your repo in Github.com.
- Copy the `git remote add origin` line and run it.
- `git push origin master` to push the code to Github.

You should be ready to continue with the assignment.
