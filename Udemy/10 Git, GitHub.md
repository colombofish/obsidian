Git helps to maintain multiple versions of files and enables to go back to the desired version. 
To initialize type `git init` in a folder, where you wanna have the version control. This folder is called the Working Directory. We can specify the files, which need to go into the Staging area, which is an intermediate state, by using cmd `git add fileName`. 
Use cmd `git status` to check which of the files are in the staging area. 
Use cmd `git commit -m "Some comment"` \[use present tense for commit messages]. `commit` allows to store files into the git repository. 
Use cmd `git log` to see which commits are done. 
Note: `git add .` here, the '.' represents all files in the current folder to add. 
Next, we can `git commit ....`. If more than one commits are done, we will see the latest commit mentioned as (HEAD -> master).
Use cmd `git checkout filename` to remove 'filename' from the staging area, in case something got messed up with that file or other reasons. 
Use `git rm --cached -r .` to remove everything from the staging area, where r is for recursive.
Use cmd `git diff filename` to see what's the difference of the current version and before the current modification. 
*Note*: to create a file `touch filename`, then to open it in VSC `code filename`

So, GIT is a local repository. If we wanna publish it on Internet, then use GITHUB. 
Once you're logged in:
1. create a new repository (give a name, description, Readme file is not required to add)
2. Once a repository is created, we can either use Desktop or use Command Line for posting (note the HTTPS/SSH options and select appropriately depending on the settings. One of them should work). So, follow the online instructions on the github page to push the files.
3. Once uploade, you can go to Insights -> Network, you will see the main/yoursettings saved points as progress of the repository. 
So it can go from Working Directory => Staging Area => Local Repository => Remote Repository.
==To reset new origin:  `git remote set-url origin https://github.com/colombofish/...git`==
#### .gitignore
Suppose, we have many files along with secrets.txt file, which we don't wanna send to the public platforms such as GitHub. Similarly, the OS generated files, user settings, user preferences etc. Hence, to avoid sending unwanted files to GitHub, create a hidden file called `.gitignore`, and add all filenames, that you want to ignore adding and committing to Git. 
You can use `#` to comment or `*.txt` wildcard within .gitignore

Useful .gitignore templates `https://github.com/github/gitignore`, which can be copied and saved into .gitignore file. Ex: Node.gitignore content into .gitignore, so it won't copy the node_modules folder and other unnecessary folders and files if we have them within our project folder.

### Cloning
Here, Cloning from GitHub to our local machine. `git clone url`. {url is typically from GitHub} Ex: if we find an interesting product, on which we wanna customize with our own versions and modifications, cloning helps to resume from where it is left, or if there is an open source project, and if we wanna contribute to it, then also we can clone and modify and post it back if required. Or we can host our own Email Server ex: MailChimp etc. A sample collection of repositories: https://github.com/awesome-selfhosted/awesome-selfhosted
Evershop: = {db: my_evership, user: postgres, password: M...1!, fullName: Admin, adminEmail: admin@admin.com, adminPassword: Nil..1}