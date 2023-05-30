#Git and GitHub

Guide to git and github commands I have used.

##git init
initializes git at the folder

##git add
adds a file to the scope of a git commit

##git rm <filename>
removes a file from the folder and grom git
	
	use --cached to make it only delete it from the scope of a git commit, but not remove the file itself
	trick: if you made changes to .gitignore and want to apply it through the project, use git rm -cached to delete everything, and then use git add . to stage everything that is not ignored by git, thus being able to delete all the files that you don't want git to track by committing whatever is staged

##git cat-file
	
	instruction -p

##git status
	shows the commited/uncommited status of the files within the repository and whether they are in the scope of the git commit

##git commit -m "message"
	commits files in the scope, adding a message. if you don't add -m, it will open a text editor and ask you to edit the message first

##git config --global user.email "myemail@email.com"
	sets email for global user. Can also be --local or --system

##git config --global user.name "myusername"
	sets name for global user. Can also be --local or --system

##git config --list
	lists the git configurations

##echo "text to hash" | git hash-object --stdin
	using the content from before the pipe as "parameter" for the command after the pipe

##cat <filename>
	show text content of a file

##git log <branch name>
	shows the log of changes to the branch (use master by default)

##git checkout or git switch <branch name> 
	
	moves to a different branch or commit
	this will change the HEAD file in .git to refer to the active branch

	if going to a previous commit instead of the current state of a given branch, use the hashcode of that commit instead of the branch name (you can also use HEAD~n, where n = number of commits in the past - only considering the current branch or master). if you do that, add to the command the instruction:
	
	--detach
	
	Commits made in a detached state WILL BE LOST as soon as you checkout to a branch

	use instruction -b to create a new branch with that checkout

##git restore .
	delete all uncommited changes

##git branch <branch name>
	creates a branch

	use -d instruction to delete a branch that has already been merged
	use -D instruction to delete a branch that has not been merged
	use -a instruction without branch name to tell the current active branch name

##git reset HEAD~<number of commits>
	resets the HEAD, cancelling a number of commits, but not deleting the changes and files, although they will not be staged

	use --soft instruction to cancel the commit but keep the changes staged
	use --hard instruction to cancel the commit and delete all changes

	if you cancel a commit wrongly, look for the reference to this commit using:

	git reflog
		it will show you all ations done before and their commit references

##git merge <branchname> -m "message"
	merges the <branchname> into the current branch. Both will now point to the same commit hash

##git rebase <branchname or commit hash>
	rebases the current branch to a particular branch or commit
	git will change the parent commit of your branch to the selected commit, and reapply all the commits of your current branch. It may result in conflicts that you will have to resolve

##git stash save "quick description or identifier of the change"
	saves the uncommited changes that are staged, allowing you to switch branches without losing the unfisnished changes

	use -u instruction to also include untracked files (although... why? just track them :) )

##git stash list
	lists the available stashs with their IDs

##git stash apply <stash ID>
	applies the changes contained in a specific stash

##git stash drop
	deletes a specific stash

##git stash clear
	deletes all the stashes

##git clone <https URL>
	clones a github repo

##gpg --full-generate-key
	generates a public and a private key to authenticate your user.

	gpg --list-keys
		lists all existing public keys
	gpg --list-secret-keys
		lists all existing private keys
	gpg -a --export <Hash ID for the key>
		echoes the public key. Use "> filename.extension" to save the output to a file instead of just echoing it in the terminal
	gpg -a --export-secret-key <Hash ID for the key>
		echoes the private key. Use "> filename.extension" to save the output to a file instead of just echoing it in the terminal
	
	after that, on github > profile > settings > SSH and GPG keys, add the public key

	on git config, set --global user name and email, commit.gpgsign true and user.signingKey <Hash ID for the key>

	gpg config = gpgconf
		see https://manpages.ubuntu.com/manpages/bionic/man1/gpgconf.1.html

--------------

##.gitignore
	create a .gitignore file containing the instructions to what should be ignored by git, example:
	*.log

	commit this file and make ir part of your project 

##GIT DB objects (unique hash codes for each)
	
	Blob - files
	Trees - folders
	Commit - data for the commit, reference of the tree object

##garbage colletor turn objects into packs, still recoverable

##Bash commands

cd
cp - duplicate file
mkdir
remove
pwd
touch
echo