# Learning Git & GitHub

## What is Git
Let's take about what Git is and what makes it different.
- **Track changes over time**
	- Git is a tool to help you track changes over time. 
- **Backup & restore**
	- It lets you backup and restore files from different key points in a project's history. 
- **Distributed version control**
	- It's known as Distributed version control because it's designed to be used by multiple users. 
- **Designed for multiple editors**
	- Each user can have a complete copy of the entire project locally, allowing them to work even offline. Git provides tools for managing changes users create on similar files.

---

## Multiverse Time Machine
In essence, Git is a multiverse time machine, somewhat similar to what you see in Marvel or Star Trek movies. It lets you travel back in time to difference checkpoints you save and lets you create alternative timelines to try out new code.

- **Repo** (repository)
	- The place where the data is stored is called a **repository** or **repo** for short. This data is stored in an **invisible** folder that keeps the **history** of the changes made to the files. Git only keeps track of original files and any changes that have been made to them. Repositories can be stored **locally** or **remotely**.
- **Check points** (commits)
	- With Git, you can **lock in** time codes that you may want to go back to go back to later on. These are known as **commits**. Each commit will have an **ID**, and store the current status of all of the files in the tracked folder.
- **Alternate history** (branches)
	- You can create an **alternate history** of the project by creating different **branches**. That creates a new universe where you or others can experiment without messing up the main version of the project. You can create as many branches as you like. Branches are the preferred way of making changes to your content because it leaves the original untouched.
- **Synchronization** (merging)
	- When you're ready to lock in the changes on the official (main) version of the project, you perform a **merge** command. That allows you to **synchronize** the different versions and bring the main branch up to date.
- **Publishing** (pull/push)
	- Projects are usually published on a remote server, know as the **origin**, which allows many people to have access to the project. As an individual you can pull to get information from the server, or push to send your changes.
- **Releasing** (Pull Requests/Discussions)
	- To deploy projects officially, you go through a process of updating the repository on the cloud through a process often called Gitflow. You issue a request for the changes to be added to the released softare (**pull request**) and discuss the proposed changes with your team, then the changes get merged on the remote repository.

---

## Local vs Cloud
In this class and in GitHub in general, you can use Git in one of two ways.
- Work locally, publish on the Cloud
- Work and Publish on the Cloud using [[GitHub CodeSpaces](https://github.com/features/codespaces)]

---

## Local Configuration
You can install Git locally by [downloading the git downloader]([url](https://git-scm.com)) on a PC. For a mac, you'll need to install x-code (app store), [homebrew]([url](https://brew.sh/)) and then the git client through homebrew. I [created a video]([url](https://youtu.be/2T_zWr5n8RE)) for you.

Once you do that, you'll need to use a terminal or the GitBash application that came with the Git Installation. Then you need to run these two commands.

```sh
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```

You may also want to install [Visual Studio Code]([url](https://code.visualstudio.com/)) or use any other editor you're comfortable with.


---

## Local Setup
Once you've downloaded and installed Git, there's a few basic set up commands you should be familiar with.

- `git init`
	- The `git init` command creates an invisible `.git` folder, which git uses to store the changes to the files being tracked by the application.
- `git status`
	- The `git status` command shows the status of your files. 
	- Shows detailed description of where documents are in the git process.
	- Shows hints about how to change things.
- `rm -r .git`
	- You can ask git not to track your files any longer by removing the `.git` folder using `rm -r .git`. This can be dangerous because it removes all history, but it can also be beneficial when you are starting a new project based on an old one or want to start your history fresh.

---
## Cloud Setup
In addition to settings things up locally, you'll need to set things up in the cloud, the easiest way to do that is to go to github.new.

- Template
	- You may choose a template, which lets you base a new project on an existing project (more on setting this up later.)
- Owner/Repository Name
	- Next, you have to choose which owner is in charge of this repo so that it's associated with that account, then give the repository a name. There are some limits to how you can name things. For example, you can't use spaces, so underscores and hyphens are common.
Description
	- The description is important because that's how you'll identify this repo when you're searching for it.
- Public/Private
	- This option will determine which features are available, specially on free plans. For this class, use public.
- README
	You can ask a repo to include a README file. The first document people see when they look at the repo. Ignore this if you have a local file.
- `.gitignore` 
	- This is a special invisible file that will tell GitHub NOT to upload certain files or folders to the server. Important to avoid passwords and local setup files from uploading.
- license
	- The license file tells people browsing on GitHub the permissions you're giving to the files and how to use them. The regular (non-enterprise) GitHub is meant to be a place where people can comment on public code.


---

## Connecting to Remote
You can connect a local repo to a remote location like Github using the remote commands.
- `git remote add <remote-name> https://github.com/<username>/<reponame>.git`
	- The remote command is how we manage our connections to other places. 
	- The traditional `remote-name` is `origin` and it will be the default if you clone a repo from GitHub.
	- After the `remote-name` is the URL to Github, this usually have your `username` and `repository` name, but it can also have an `organization` name. It should also always end with `.git`
	- You can add multiple remotes if you want to 
- `git push -u <remote-name> main`
	- In addition to connecting to the remote, you also have to connect branches with their counterparts on GitHub.
	- The `-u` sets the default upstream branch for a branch, making pull and git push operations so you don't have to specify the remote and branch each time.
	- You can also push all branches to the remote with `git push --all`

### Exercises
Lets connect our local repository to our GitHub repo.
- **Copy** the URL to your GitHub repository
- On your local copy of the repo, type in `https://github.com/<username>/<reponame>.git` using your username and reponame.
- Issue a `git push -u origin main` to push your main directory
- Go back to your GitHub Repo and see the updated repo.

---

## Working Directory

The working directory is the folder where you `.git` folder lives and contain the files git is tracking. Files in the working directory can be in different states.

- **Untracked**
	- You can have files in your git folder that are not yet part of the repository, these are known as untracked files. 
		- These files are not included or stored in the history. 
		- This can happen when you first create a repo
		- It will also happen when you copy or create new documents inside the repo folder.
- **Modified**
	- If a file has previously been committed and is then changed, then it's going to be in a modified state. 
	- It can be reverted back to its original state or staged for later committing.
- **Staged**
	- Modified files can be moved into a temporary queue called staging. 
	- This will let you store changed files to keep track of what will be committed. 
	- Files can move from staging back to working. To stage files, you can use the `add` command.
- **Committed**
	- This is the process of saving changes in staging to history, locking in a place that you can always come back to. 
	- It stores  the name and email of the person who made the commit, the date when the commit was made, a user message and an ID for the commit. 
	- After the changed files will be in a working state.


---

## Staging Files

Let's talk about the process of moving files into the staging state. There's a few [commands](https://git-scm.com/docs/git-add) you can use. 

- `git add <filename>`
	- This allows you to move one or more files to staging. 
	- You can stage individual files by using git add and then specifying a filename you want to add.
	- That filename can support any file glob or shortcut.
- `git add .` `git add *` `git add --all` `git add -A`
	- If you want to move all modified or untracked files to staging, these commands will add all of the modified files into staging. 
	- This is probably one of the most common way to add files. 
	- You can of course use any file shortcut like `*.js` to add all of the javascript files in the current directory.
- `git rm --cached <filename>` `git restore -S <filename>`
	- These command let you move files out of staging and back into untracked. 
	- If you add the `-r` option, it will recursively let you remove a bunch of files at once. 
	- It's a bit hard to remember, but you can always let the `git status` command remind you.

### Exercise

Let's practice moving files in and out of staging.
- Stage a single file using `git add <filename>`
- Unstage a file using `git restore --staged <filename>`
- Stage all files using `git add .`, `git add *`, `git add --all` or `git add -A`
- Unstage all of the images using `git rm -r --cached images/**`
- Re-stage all the images using `git add .`

---

## Committing files

To create a commit, you can issue a [commit command](https://git-scm.com/docs/git-commit). this saves staging to history, locking in a place that you can come back to. After the changes files will be in a working state.

* `git commit -m "Message"`
	- You can commit files using the `git commit` command, it requires that you give it a message recording what you're doing.
	- The message acts as a label you'll see when going over a list of commits.
	- It can be quite complex and include the changes you've made to the files since the last commit, but the most important part is the label, since it's what you'll see most often.
	- The shortcut for the `--message` option is `-m`
- `git commit -m --dry-run "Message"`
	- The `--dry-run` option lets you take a look at the changes you're making, so it might be helpful when writing your message.
- `git add . && git commit -m "Message"`
	- Some people will use the double ampersands to queue up two git commands together, specially the add and commit commands.
- `git log`
	- Lets you look at the history of commits: It stores  the name and email of the person who made the commit, the date when the commit was made, a user message and an ID for the commit.

### Exercise

Let's try committing all of the files from staging with `git commit -m "Initial Commit"`

- The `-m` is required and lets you add a message to your commits. It's a shortcut for --message.
- Let's issue a git status command to see what's going on `git status`

Now we have a clean working tree.
`git log`, then `q`

Lets take a look at the information that Git is saving about our project. You can scroll down to see a longer list and hit the `q` key to continue.

---

## Ammending Commits

An amend will add modified information or changed files to an existing commit.

- `git commit -m --amend "Message"`
	- You use it if you forget to commit something or want to make some minor modifications to a commit.
	- This is also a way to change the commit message, if you made a typo or want to add some context
	- **Warning!** This does not add untracked files to your commit, so if you have created or copied new files, you'll need to add them first.
	- **Warning!** This is good for local commits, or when working solo, but can be dangerous when working in a team environment, if someone has work based on the previous version of a commit.
-  `git commit -am "Message"`
	- You can use `-a` as the shortcut for the amend command.
- `git commit -am --no-edit`
	- The `--no-edit` option leaves the old commit message unchanged.

### Exercise

Let's try adding a `README.md` file to our project, I [created one](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) for you.

- Don't copy all of the text, start by copying only the **Title and Description** in the [README.md](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) gist.
- `git add .` and `git commit -m "Message"` the file with a simple message
- Issue a `git log` command to see information about your commit.

#### Practice a no-edit option

Using a no-edit option to add to an existing commit

- Copy the [next section](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) of text to the file titled **Techniques Used** and Paste them into the `README.md` file.
- Save it and do a `git status` to see that the file is currently listed as modified.
- Add the file using `git add README.md`
- Issue the `git commit --amend --no-edit` command to add the changes.
- **Note:** Remember that this works well for solo developers, but when working with a team pushing amends could cause problems for those who already pulled a previously committed history.

#### Untracked files
Untracked files will sometimes cause unexpected behaviors when committing and amending.
- Copy the [next section](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) of text to the file titled **Notable Libraries and Technologies** and Paste them into the `README.md` file.
- Add the file using `git add .`
- Now, create a new document on the same folder called `LICENSE.txt`. Add this [MIT license](https://gist.githubusercontent.com/planetoftheweb/7e254040a0525971c45295ddabf25e84/raw/b45be12298e44c52b241cdd759c703b404b48220/LICENSE.txt) to the document, then update it with the year and your name.
- Now you should have one untracked file and one modified file. Let's see what happens if you commit.
- Try a `git commit -m "Modified README and added a LICENSE"`.
- Issue a `git status` command. Notice that because the `LICENSE.txt` file was untracked, it wasn't committed and you didn't get any sort of error message.
- Now, let's use `git add .` LICENSE file and `git commit --amend --no-edit` to add the license and add it to our last commit.
- Issue a `git status` and `git log` command to verify the changes were logged in properly.

##### Note
I created this [README](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) using [Chat GPT](https://chatgpt.com/) and [this prompt](https://gist.githubusercontent.com/planetoftheweb/ddbf48aa93b6eac6508aaf690f03f236/raw/39489319b1ca054986e65600d3d525f8364c1da5/README%2520prompt%2520generator). AI is a great way to generate things like README files and other documentation about your project.

---

## Restoring Files
This command lets you revert changes in the working directory and staging area. It makes it easy to revert files to a previous version.

- `git restore <filename>`
	- This command discards changes in the working directory. It's a newer command with a single purpose.
- `git checkout <filename>`
	- This does the same as git restore and is a popular older version of the command. Checkout allows you to do other things as well.
- `git restore --staged <filename>`
	- The `--staged` option will also **unstage** the files.
- `git restore --source <commit> <filename>`
	- You can also restore a file to a different commit, so if you want to bring a file back from a previous version you can do that by including a commit hash id.

### Exercise

Let's try the restore command a few different ways.

#### Restore to last commit

- Copy the [next section](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md) of the `README` file titled `Notable Libraries and Technologies` and paste it into the `README.md` document.
- Make sure you save the file.
- Use the `git status` command and notice that it lists a modified file not staged for commit.
- Use the `git restore README.md` command.
- Git restores the previous version of the file.

#### Using the --staged option

`git restore` doesn't work on staged files, so to restore that you have to use the `--staged` option.
- Paste the section of the file again (or use undo) to update the `README.me` file.
- Issue a `git add . command` to stage the file
- Try issuing a `git restore` command. Notice the file still has the new changes.
- Run `git status` and notice that the file is still in staging ready to be committed because restore by itself won't have an effect without the `--staged` option.
- Run the `git restore --staged .` command, and you can see that the period command will restore all the staged files, but leave the changes.
- If you want to get rid of the changes, issue the `git restore .` command.
- Go ahead and add the changes, then commit them as a new commit called "Added Notable Libraries and Technologies"

#### Restoring a different commit

You can also restore a previous version from an older commit.
- Select everything in your `README.md` file and `delete` the content, then `save` the file.
- Issue a `git log --oneline` and copy the **hash ID** for a previous commit.
- git `restore --source <hash_id> README.md`
- Try restoring to a different ID.
- When you're done, use `git checkout .` to get the  version of the file from the last commit.

---

## Rewriting History

When you make a mistake, you can use the [git reset](https://git-scm.com/docs/git-reset) command to reset history to a previous commit ID. This rewrites the position of the HEAD pointer, whereas restore leaves it alone.

- **HEAD pointer**
	- When you use the git log command, you'll noice that there's something called a HEAD pointer at the top of your commit messages. This represents the tip of your current branch.
- `git reset HEAD~1`
	- The default mode for resetting is called mixed mode, so this is the same as adding a `--mixed` option.
	- The `HEAD~1` part tells git to go back one commit. You can of course go back more than one commit. If you want to go back to a specific commit, you can also include a hash of the commit instead of `HEAD~1`.
	- This will reset your commit to the previous version.
	- It also un-stages the files, but it doesn't get rid of any changes you made, it leaves the files changed as modified.
- `git reset --soft HEAD~1`
	- The **--soft** option does the same thing, but it leaves files in staging instead of as modified or untracked.
- `git reset --hard HEAD~1`
	- The `--hard` option gets rid of all changes in staging and the working directory.

### Exercise

Let's practice using these different options.

#### Mixed Reset
- Modify the `README.md` file to include a new headline `## Bogus Info` 
- Make sure you save the file.
- Issue a `git add .` and `git commit "bogus commit"`
- Issue a `git log --oneline` command to verify the new commit is in history and hit `q` to exit the log.
- Now, let's use a `git reset HEAD~1` command.
- Notice the file keeps the `Bogus Info` headline
- Issue a `git status` command to verify the README.md file is not staged for commit.

#### Soft Reset
- Issue a `git add .` and `git commit "bogus commit"`
- Issue a `git --oneline` command to verify the new commit and hit `q` to exit the log.
- Issue a `git reset --soft HEAD~1` to reset the file.
- Issue a `git status` command and note that `README.md` file is in the staging area ready to be committed.

#### Hard Reset to a Specific Commit
- Let's add some extra text under the `Bogus Info` headline with the text `Additional bogus information` 
- Make sure you save the file.
- Issue a `git add . && git commit -m "Additional bogus commit"` command.
- Issue a `git log --oneline` to make sure the new commit exists.
- Copy the short hash id (i.e. d697c6f) to the commit you want to revert to, then hit the `q` key to exit.
- Issue a `git reset --hard ID` where the ID is the number you copied.
- Notice all your changes have been removed.
- Issue a `git log --online` to verify the bogus commits are gone.

---

## Ignoring Files
When working with projects, sometimes you want to prevent certain files or patterns of files to be ignored. To do that you can create a special dot file

- **Root Level**
	- The `.gitignore` file should be added to the root of your project.
- **Files, Folders and Globs**
	- It can list individual files, folders or file patterns that you want git and GitHub to ignore, so these will not be pushed onto GitHub.
- `.DS_Store`, `Authentication.js`, `dist`, `build`, `node_modules/`, `logs/*.log`, `.env`, `**/*_note.md`
	- Here's some common `.gititnore` files
	- `.DS_Store` is a hidden mac file that is not relevant to your project, but might be added by the OS. 
	- `Authentication.js` or similar files are documents that you might need in order to work with external APIs. They're named different things, so adjust as needed.
	- , `dist/`, `build/` are folders that different tools will create for you and sometimes you don't want the generated folders to copy to a server.
	- `node_modules/` is a folder with dependencies that are common for web projects.
	- Some projects create log files, so `logs/*.log` is also a good thing to add here.
	- `.env` environment files provide a way for you to 
	- You can create your own set of files that will not upload. `**/*_note.md` 

### Exercise
Create a new `.gitignore` file at the root level of your project.
- Add any files or globs that you think your project might use.
- Add a `**/*_note.md` glob to exclude any files with the `_note.md` extension.
- Use the `git add .` and `git commit -m "Added a .gitignore file"` commands to add and commit the file.
- Create a `main_note.md` file
- Use the `git status` command and note that it says there's nothing to commit.
- Create folder called `notes` and add a `local_note.md` file inside it.
- Use the `git status` command and it should also say that there's nothing to commit.

#### Note
Empty folders are not tracked or uploaded to GitHub. If you want to makes sure a folder gets uploaded to GitHub, you can just add a `.gitignore` or any other dot file like `.gitkeep`, even if they're empty.

---

## Creating Branches
So far, we've been working by making changes to the main branch. The traditional way to work with project is to leave the main branch alone and do your work in a separate branch. This is known as Gitflow.
- `git branch` 
	- Shows you the current branches in the project, the default branch is traditionally called `main` or `master`.
	- A branch copies all of the previous commit history from the branch it is issued from.
- `git branch <name>`
	- This creates a new branch with a name. Traditionally the name refers to a feature we want to work on and is sometimes called a feature branch.
- `git checkout <name>` `git switch <name>`
	- These commands allow you to go to a specific branch.
- `git switch -c <name>` `git checkout -b <name>`
	- You can also create branches and switch to them immediately with these options. 
	- Switch is considered a newer, clearer version of the command and the -c version stands for create.
	- A lot of people use checkout and if you add the -b for branch option, you can create and switch just like with switch.
- `git branch -D <name>` 
	- You can delete a branch with the -d option
	- It's common to delete a branch once you're finished with a feature and it has been merged back into the main branch.
- `git branch -m <original_name> <new_name>`
	- If you want to rename a branch, you can use the move option and add the original name and the new name.

### Exercise
Let's practice creating and navigating through branches.

#### Creating Branches
- Issue the `git branch` command to take a look at the current available branches, there should only be a single branch.
- Create a new branch using `git branch add_fonts`
- Switch to the new branch using `git switch add_fonts`
- Issue a `git log --oneline` command and notice that all of the commit history has been copied from the main branch.

#### Modifying Branches
- Add the section titled `Fonts` to the `README.md` document.
- Issue `git add .` and `git commit -m "Added Fonts Section"` commands to create a new commit.
- Issue a `git log --oneline` command to see the log and notice the place where a new branch was created and the position of the HEAD pointer. Hit `q` to exit the log.
- Issue a `git checkout main` command to go back to the main branch. Notice the changes are gone.
- Issue a `git log --oneline` command to see that the log doesn't have the changes.

#### Deleting branches
- Switch back to the previous branch with `git switch add_fonts`
- Create and switch to a new branch using `git switch -c new_branch` 
- Issue a `git log --oneline` and notice that it copied the last commit. Hit `q` to exit the log.
- Issue a `git switch main` command to switch back tot he main branch.
- Use `git branch -D new_branch` to delete the new_branch

---

## Merging Branches
Merging allows you to integrate changes from one branch to another. It's often used to move things from feature branches onto the main branch.
- `git merge <source-branch>`
	- The merge is always done into the current branch, so this command would add changes from the from the `source-branch` into the current branch
	- This is know as a `fast forward` merge and is the simplest type of merge you can do.
- `git log --graph` is a version of git log that shows the flow of the merges.
- Merges can be of different types and require different approaches when you need to resolve them.

### Exercises
Let's practice some merging of our projects. I'm assuming you still have a branch called add_fonts with the fonts section of the README file.

#### Straightforward Merge
Lets create a straightforward merge
- Issue a `git branch` command to get a list of branches and verify that you still have the `add_fonts` branch.
- If you're not in the main branch, issue a `git switch main` command to make sure you're on the main branch.
- Issue a git merge `add_fonts` command to add the changes in `add_fonts` to your `main` branch.
- Use a `git log --graph` to see the flow of the commit.

#### Merge with a conflict
Sometimes, you can try to merge a branch, but you've already made changes to the branch you want to merge into, so a different approach is necessary.

- Assuming you're in the `main` branch and that you still have a branch called `add_fonts`.
- Issue a `git log --oneline` and look for the commit hash ID that's before the commit where you added the fonts.
- Issue a `git reset --hard <hash_id>` to reset back to that commit.
- Now, let's say that you wan to change the title of the section from `Project Structure` to `Repo Structure`. Go ahead and make that edit and save the file.
- Issue a `git add . && git commit -m "Modified Title"` command.
- Now, let's try to merge the work we did in add fonts and remember that our main branch is currently ahead of that branch, so issue a `git merge add_fonts`
- You will get the option of adding a merge message. You can edit it if you like, but to get rid of it, you can simply close the window or the file in your default editor.
- **Notice** that git merged the two files and the two commits and it did so using an 'ort' strategy.
- Issue a `git log --graph` to visually see the two commits being merged into main.
- **Warning!** Sometimes, git will ask you to verify or write a commit message in an editor. The default editor will depend on your operating system. 
	- After you install Visual Studio Code, make sure you use the command palete and look for the
	- - Select **Shell Command: Install 'Code' command in path** from the Command Palette.
	- **Mac:** `shift + ⌘ + P` while inside VS Code **Windows:** `shift + ctrl + P`, make sure you select **Add to PATH** during the installation.
	- You can set up the default editor to be Visual Studio code using this command: `git config --global core.editor "code --wait"`

#### Merging Two Branches with Changes
You can also resolve changes in different branches
- Issue a `git log --oneline` to get a list of the hash IDs for your commits. Copy the hash ID for the commit before you added the fonts section. Hit `q` to return.
- Issue a `git reset --hard <hash ID>` command to revert to that commit.
- Use the `git checkout -b key_features` to create a new branch.
- Copy and paste the `Key Feature` section [from the file](https://gist.githubusercontent.com/planetoftheweb/aa7731b1d782082f71b38cc89ff4d9de/raw/038609b40822b6388d176d22a2c0c06a219f4f7d/README.md).
- Use the `git add . && git commit -m "Key Features" ` to create a commit.
- Use `git switch main` to go to the main branch
- Use `git merge key_features` to merge the newer branch.
- Use `git merge add_fonts` to merge the add_fonts branch.
- Now you have a **merge conflict**, which you need to resolve. Visual Studio code gives you some shortcuts you can use to accept the current change, the incoming change, or both changes.
- Because we want both changes, but they're not in the right order, we'll need to edit the file to make sure it's in the right order.
- Edit the file so it has the `Fonts` section, then the `Key Features` section.
- Use `git add .` and `git commit -m "Added Fonts and Key Features"` to add both changes.
- Use the `git log --graph` to see the commit graph history. Hit `q` to exit.

---

## GitFlow
GitFlow is the process of updating things safely with Git. We've been practicing it locally, but you can do the same thing on Github. You create a branch, make changes on the branch and merge the changes to that branch onto the main branch.

### Pull Requests
On GitHub normally you perform one additional task in this process and that is called a Pull Request. Pull requests are formal requests for changes to be added to a website.

### Using the Website
You can use the website to add, delete and edit files directly without having to jump into a Codespace. Remember you can easily drag and drop documents and add folders or files.

### Exercise
To practice GitFlow, we'll use the website to add a default [settings.json](https://gist.githubusercontent.com/planetoftheweb/b840d7dad358cf1b79e543bfe3d8a036/raw/6b295971394e1c79fe58d5686fb8a6d2a044e22e/settings.json) file. This file will set up some defaults for Visual Studio code on this repository. The settings will automatically be used when you run a CodeSpace.

#### Adding a file
1. Go to the link for the [settings.json](https://gist.githubusercontent.com/planetoftheweb/b840d7dad358cf1b79e543bfe3d8a036/raw/6b295971394e1c79fe58d5686fb8a6d2a044e22e/settings.json) file.
2. Copy the text
3. Go to the repo for your site
4. The settings.json file needs to be inside a folder called `.vscode/`. To create a folder click on the `Add file` button.
5. Click on `Create new file`
6. Paste the contents of `settings.json`
7. At the top of the code, look for where you name your file.
8. Type in `.vscode` and hit the `/` key, it will create a new directory.
9. Name your file `settings.json`
10. Hit the `Commit changes...` button
11. You can leave the commit message and description alone if you want
12. Choose `Create a new branch for this commit and start a pull request`
13. Type in a name for the branch `add-settings`
14. Hit `Propose changes`
#### Using the pull request
That creates your branch and initiates a pull request. A pull request gives you an opportunity to discuss changes that are being proposed to the code before they get merged back to another branch.
This gives also gives you an opportunity to add reviewers, assignees, labels, projects, etc.
1. You can leave the title and description alone for now. 
2. Under Assignees, choose `assign yourself`
3. Under labels pick `enhancement` from the list.
4. Click on `Create pull request`

This will generate the pull request. Notice it also logged what you did, the adding of the file, the tag and your assignments.

Take a look around and notice the `commits`, `checks` and the `files changed` tabs.
#### Merge the pull request
You or other collaborators can add a comment to the pull request if you want to or simply merge the pull request to merge things into main.
1. Hit the `Merge pull request` button
2. Hit the `Confirm merge` button
3. Hit the `delete branch` button

The pull request will me merged into main and closed. Click on the `pull requests` tab and notice it says `0 Open` and `1 Closed`. You can still go back to the closed pull request if you want to know what it's all about.
#### Using the temporary editor
1. Go back in o the `code` tab.
2. Notice the `.vscode` folder is now there.
3. Hit the period key `.` on your keyboard.
4. This launches a quick version of the editor that is like a Codespace, but without the ability to run build processes on the terminal.
5. Examine the `settings.json` file in this editor.
6. Try changing some of the settings
7. Close the window to ignore the changes.

---

## Issues
Issues are a way to create a document that people can discuss and contribute to. They are similar to pull requests but a bit more flexible.
### Create an Issue
1. Go to the Issues Tab
2. Click on `New issue`
3. In the title write "Add Instructions"
4. In the description use: `Add instructions to edit the HTML file to customize this for your own artwork.`
5. Click on `Assign yourself`
6. Add a `documentation` and `enhancement` label
7. Hit submit new issue

### Using AI to Create Documentation
AI Tools are great at helping you write documentation or code. 
1. Go back to your site's `code` tab
2. Click on the `local button` 
3. Click on the `Index.html` file.
4. Click on the `raw` file button
5. From the `file` menu in your browser hit the `save` button
6. Go to `chatgpt.com`
7. Drag the file to the Chat GPT window
8. Type in the following prompt: `Write some instructions using markdown to help people who want to use this code update it with their own images. Save it to a file`

### Updating the site
1. Go to the Issue you created to Add Instructions
2. Look for the `Create a branch` link on the sidebar
3. You can leave the name alone, but under what's next, choose open in codespace
4. Hit the `Create branch` button.
5. Hit the `Create codespace on <NAME>` button

### Using the Codespace
1. Create a `docs` folder
2. Upload the `update_instructions.md` file into the docs folder.
3. Open the README document.
4. Add the instructions at the end of the file. Check out [these instructions](docs/update_instructions.md)

### Using Source Control
1. Switch to the source control icon on the left toolbar
2. Type in a commit message "updating docs"
3. Hit the `commit` button
4. Tell it to `always` stage and commit changes.
5. Click on the `Sync Changes` button, then click OK.
6. Optionally you can ask VSCode to periodically run `git fetch`

### Compare and Pull Request
When you come back to the site, you'll see an option to compare and pull request.
1. Hit the `Compare and pull request` button
2. Scroll down to review the changes.
3. Hit the `Create a pull request` button
4. Hit the `Merge pull request` button
5. Hit the `Confirm merge` button
6. Hit the `Delete branch` button
7. Optionally delete the codespace.

Now you can go back to the code page on the repo and see the changes. This will also automatically close the issue.

---

## Forking
Forks are a way of creating an alternate version of an existing project.
- Common for modifying a 3rd party project
- You can make changes that your work get added to the original project
- Create a pull request to suggest the changes
- Members can discuss and accept external changes
- Your work can be merged into the main project

### Exercise
Create a fork of a project.
- Go to [this project ](https://github.com/planetoftheweb/demo-forking-01)
- Click on the `fork` button
- Choose an `owner`
- Git the forked repository a `name`
- Click on the `Create fork` button

### Exercise
Modify the existing fork
- On the fork you just created, go to the `code  tab`
- Scroll down to the `pencil button` on the README file.
- Add "completed by `Name`" under the heading Completions
- Hit the `Commit changes` button
- On the Pop-up, also hit the `Commit changes` button

### Exercise
Contribute your change to the original
- On the code page, click on the `Contribute` dropdown
- Click on the `Open pull request` button
- Add a title "Adding `<yourname>` to the project"
- Hit the `Create pull request` button
