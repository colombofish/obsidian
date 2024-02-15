download from https://gitforwindows.org
##### Git Bash
after installing with the default settings, open vscode, open terminal, and invoke GitBash from the dropdown menu from the terminal menu. You should see the $ sign. Now to link this bash to vscode do the following:

Command Palette -> Search for 'select default profile' -> select 'Git bash'. This will make the Git bash as the selected terminal.
In the command line a cool trick is to press 'Alt' and then can point the mouse where you want to edit the cmd. Other UNIX shortcuts like 'Ctrl' + a (to go to the start) or 'Ctrl' + e (to the end); 'Ctrl' + U to clear the line etc can be handy. 
'rm -r' this remove entire directory and all child folders etc. 
for more cmds, refer to: https://www.learnenough.com/command-line-tutorial
#### Git
`git init` // to initialize git repository. This will create a '.git' hidden folder in that working dir.
To track the files in a working dir., we need to add the file to staging area.
`git status` // shows which files are added into the staging area, and which are not.
`git add chapter1.txt` //adds chapter1.txt into the staging area. use 'git status' to check it.
`git commit -m "version ctrl message"` //To save into the repository with the message.
*By convention use the simple present tense within the message. Not past*
`git log` //This gives a report of the changes/commit made
`git add .` // here the '.' specifies to add all files in the current dir. 'git log' to check it. 
*if anything got messed up in btn, we can use the last version through `git checkout` cmd.*
`git diff chapter3.txt` //shows up the changes made from the last version.
`git checkout chapter3.txt` updates/reverts the file with the last version.
`git log` //verify the log
