Create a GitHub Repository and Commit with Git Commands
This guide uses the GitHub website to create the online repository and Git in Windows Command Prompt (cmd.exe) to save and upload project changes. It does not use GitHub CLI or PowerShell commands.

1. Choose the repository name
Students should name the repository using this pattern:

rollno-firstname-webdev-day01-setup-practice
Replace <rollno> with your roll number and <firstname> with your first name. For example:

23-Asha-webdev-day01-setup-practice
Use the exact capitalization and naming rules your instructor requests.

2. Create a repository on GitHub
Sign in at github.com.

Click the + button in the top-right corner, then choose New repository.

Enter your repository name using the pattern above.

Choose Public or Private, following your instructor's directions.

Leave Add a README file, .gitignore, and license unchecked for this walkthrough. You will push the project files from your computer.

Click Create repository.

On the next page, copy the HTTPS repository URL. It will look similar to:

https://github.com/YOUR-USERNAME/23-Asha-webdev-day01-setup-practice.git
Replace the example roll number, name, and username with your own details.

3. Open Command Prompt in your project folder
Open Command Prompt (cmd.exe). Move into the folder containing your project. Use your actual folder path:

cd /d "C:\TrainX – Web Development (BTech Year 1)\webdev-day01-setup-practice"
cd means change directory. The /d option also changes the drive if the folder is on a different drive. Quotes keep paths with spaces together as one path.

See the files in the current folder:

dir
dir lists the files and folders. It is the Command Prompt equivalent of ls.

4. Add a README file
Create README.md in the project folder using an editor such as VS Code or Notepad. Example contents:

# Web Development Day 01

Practice project for setting up a web development workspace.

## Contents

- `index.html` — the project page
- `style.css` — page styles

## Run it

Open `index.html` in a web browser.
.md means Markdown. GitHub displays Markdown with formatted headings, lists, links, and code.

5. Initialize Git
If the folder is not already a Git repository, start tracking it and name the main branch main:

git init -b main
git runs Git, the version-control program.
init initializes a new local Git repository in the current folder. It creates the hidden .git data folder where Git stores history and settings.
-b is a short option meaning “branch”; it names the initial branch created by init.
main is the branch name. A branch is a line of project history. main is the common default name for the primary branch; it is not a special command or a description of the project.
If Git says the folder is already a repository, skip git init and inspect it with:

git status
6. Check the project status
git status
status reports the current branch and the state of files: untracked files, changed files, and changes staged for the next commit. Use it before and after staging so you can see what Git will include.

7. Stage files for a commit
git add .
add stages selected changes, preparing them for the next commit. It does not create a commit or upload anything.
. is the current directory. In this command, it means stage changes in this project folder and its subfolders.
You can stage one particular file instead:

git add README.md
Check which files are staged:

git status
8. Commit the staged changes
git commit -m "Add starter web development project"
commit saves the staged changes as a snapshot in your local Git history.
-m is a short option for supplying the commit message directly in the command.
The words in quotes describe the change. Use a short, clear message. The quotes keep the message together, including spaces.
A commit is saved on your computer. It is not on GitHub until you push it.

If Git asks you to configure your name and email, set the details you want recorded on commits, then repeat the commit:

git config --global user.name "Your Name"
git config --global user.email "you@example.com"
Here, config changes Git settings, --global applies the setting to your Windows user account for all repositories, and user.name / user.email are the values Git records as the author identity.

9. Connect the local project to GitHub
Add the HTTPS URL you copied from GitHub. Replace the example URL with your own:

git remote add origin https://github.com/YOUR-USERNAME/23-Asha-webdev-day01-setup-practice.git
remote manages links to other Git repositories.
add creates a new remote link.
origin is the conventional nickname for the GitHub repository. It is just a nickname; it can technically be different.
The URL tells Git where that repository is hosted.
Check that the URL is correct:

git remote -v
-v means verbose. It shows the remote names and their URLs for fetching and pushing.

If Git reports that origin already exists, update its URL instead:

git remote set-url origin https://github.com/YOUR-USERNAME/23-Asha-webdev-day01-setup-practice.git
set-url changes the URL for the existing remote named origin.

10. Push the first commit to GitHub
git push -u origin main
push uploads local commits to a remote repository.
-u is short for --set-upstream. It links your current local branch to the remote branch, so later you can usually run just git push and git pull.
origin is the remote nickname set in the previous step.
main is the branch to upload.
Git may open a browser sign-in flow or ask you to authenticate. Follow the prompts. Refresh the GitHub repository page to see your files.

11. Make another change and push it
Edit a project file, then inspect the changes:

git status
Stage the changed file (or use git add . to stage all project changes):

git add README.md
Commit it with a message describing the change:

git commit -m "Update setup instructions"
Upload the new commit:

git push
Since -u linked the branch with origin/main on the first push, you do not need to repeat those names for ordinary pushes.

The usual workflow
After the initial setup, repeat these commands whenever you want to save and upload your work:

git status
git add .
git status
git commit -m "Describe what changed"
git push
Command reference
Command	Meaning
cd /d "path"	Moves Command Prompt to a folder; /d also changes drive, and quotes protect spaces in the path
dir	Lists files and folders in the current directory
git init -b main	Creates a local Git repository with its first branch named main
git status	Shows the branch and which files are untracked, changed, or staged
git add README.md	Stages the named file for the next commit
git add .	Stages changes in the current directory and its subfolders
git commit -m "message"	Saves staged changes in local history with a description
git remote add origin URL	Connects a nickname (origin) to the GitHub repository URL
git remote -v	Shows remote names and URLs; -v means verbose
git push -u origin main	Uploads the branch and records its upstream link; -u means set upstream
git push	Uploads later commits to the linked remote branch
git log --oneline	Shows commit history compactly; --oneline asks for one short line per commit
Tips
Use Command Prompt, not PowerShell, for the commands in this guide.
Run Git commands from inside your project folder.
A commit is local until you run git push.
Check git status before committing so you know what will be included.
Never commit passwords, API keys, access tokens, or private data.
For an easy first push, create the GitHub repository without a README, .gitignore, or license. This keeps the GitHub repository empty until your local project is pushed.
All steps: short command checklist
Replace the placeholders with your own values. First create an empty GitHub repository on the website using <rollno>-<firstname>-webdev-day01-setup-practice, then copy its HTTPS URL.

cd /d "C:\path\to\your\project-folder"
dir
git init -b main
git status
git add .
git status
git commit -m "Add starter web development project"
git remote add origin https://github.com/<username>/<rollno>-<firstname>-webdev-day01-setup-practice.git
git remote -v
git push -u origin main
For each later change, run:

git status
git add .
git status
git commit -m "Describe what changed"
git push
