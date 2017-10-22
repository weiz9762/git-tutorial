# GitHub Tutorial

_by Wei Zheng_

---
## Git vs. GitHub
* Git is the system that used for version control, in other word, git helps you keep trackyour code
* GitHub is the platform that you can to share your work with others, and you can also visually see your code without using the command line

#### _GitHub need Git, but git does not required GitHub!_


---
## Initial Setup
### _How do you create a GitHub Account?_
* [Go to Github Sign Up Page](https://github.com/join?source=header) and you will see something like ![this](https://i.imgur.com/Bss1bfG.png)
* After you filled in your information, clcik the ![green button](https://i.imgur.com/AVjzXTR.png?2) "Create an account"
* You will now choose your plan, choose "Unlimited public repositories for free" !["Unlimited public repositories for free"](https://i.imgur.com/24WC8iQ.png?2)  
* Lastly, you will Tailor you experience but checking the box that applied to you ![step3](https://i.imgur.com/buAqdYv.png?2)  
#### After Setup your account, you will need create a SSH key  
### _So, How do you create a SSH key?_
* First, as you login your GitHub account, you will see something like this ![main page](github-homepage)
* Then, you will go to the top right and click your icon, and you will see ![icon](icon.png) and click the "setting"
* After you clicked setting, you the right you will see something like this ![SHH key setting](setting-page.png), go head and clicked on "SSH and GPG keys"
* As you do so, you will see SSH Keys and GPG Keys sections, on the right of SSH Keys section, clicked "New SSH key" ![New SSH keys green button](https://i.imgur.com/N2Gmfzd.png)


---
## Repository Setup
You will see something like this ![this](repo-setup.png)



---
## Workflow & Commands
#### After setting up your repository, and having some basic understand of how git works, you will learning how to "push" your work to GitHub. As shown in the table below, Git project divied to three different part: working directory, staging area and repository. 

| Working Directory | Staging Area | Repository |
| :-------------: |:-------------:|:-----:|
| Where the file stored before git add. You can makde changes to the file in working directory| Where the file stored after git add, it is a temporary space that file rest, so they can be commit anytime  | Where all the changes are being stored and saved it as commit |

### git status
_**Q: What is git status?**_  
**A: git status is the git command that helps you know the status of your files, there are three different status of file that you can find through git status**
1. Untracked: The file is in your directory, but it is not in the staging area (not ready to be commited)
2. Modified: The file was previously added, but there is change of the file (being renamed or deleted)
3. Tracked/Staged: The file is in the staging area and ready to be commit!!

### git add  
_**Q: What is git add?**_  
**A: By using git add, you add the file you want into the staging area, where works are tracked and ready to be commit**  

You can git add many ways
1. `git add filename`: you add specific file to the staging area

```bash
username:~/workspace/sep (master) $ touch sep-9 sep-10 sep-11 sep-12
username:~/workspace/sep (master) $ git add sep-11
username:~/workspace/sep (master) $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   sep-11
```

2. `git add .` : you add all the exist file to the staging area

```bash
username:~/workspace/sep (master) $ git add .
username:~/workspace/sep (master) $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   sep-9
        new file:   sep-10
        new file:   sep-11
        new file:   sep-12
```

3. `git add --all` : you add all the file, including the deleted file to the staging area 

```bash
username:~/workspace/sep (master) $ mv sep-9 sep-09
username:~/workspace/sep (master) $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   sep-10
        new file:   sep-11
        new file:   sep-12

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        sep-09

username:~/workspace/sep (master) $ git add --all
username:~/workspace/sep (master) $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   sep-09
        new file:   sep-10
        new file:   sep-11
        new file:   sep-12
```

### git commit  
_**Q: What is git commit?**_  
**A: After add you add file to the staging area, the works are tracked but it is not being commit(not being saved). Therefore, git commit saves your work and remember the changes as commits!**

The format you git commit will be `git commit -m "message/changes in the file"` it is extremely important that your message include what you changed in the file, so you or your collaborator can go back to work you have done.

```bash
username:~/workspace/sep (master) $ git commit -m "create sep-year files"
[master (root-commit) 7a6acd5] create sep-year files
 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 sep-09
 create mode 100644 sep-10
 create mode 100644 sep-11
 create mode 100644 sep-12
```

### git push
_**Q: What is git push?**_  
**A: Once you create a remote in GitHub and make connection with your local machine, you are now able to send your work to the GitHub where you can saved your work**


```bash
username:~/workspace/sep (master) $ git push
Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 285 bytes | 285.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:weiz9762/sep.git
   7a6acd5..4920eae  master -> master
```

However, every time you push your work to the GitHub, you need clarify the name of remote and the branch you want to push to. Therefore, to make your life easier, command `git push -u orgin master` helps you default you push to the orgin master, so you can just easily push your work through `git push`

---
## Rolling Back Changes
There are many times that you made mistake and accidentally add, commit or even push the file. There is not redo botton in git, but you can there are some ways that you can "fix" your mistakes

---
`git checkout -- file`: Undo the change in file
* file is the name of your file
* space is required between _git_ and _checkout_, and there are also _space_ before and after _--_
* The changes in the file will be gone immediately after the command, **so be careful of using it**

```bash
username:~/workspace/sep (master) $ git checkout -- sep-09
```
* In the command above, _spe-09_ is the file I want the changes being undo, and table before showing the texts in the sep-09 before and after the command

| File before git checkout | File after git checkout |
|:------------------------:|:-----------------------:|
|This is all the new changes in the file| |

---
`git reset HEAD file`: Unstage the file from staging area  
```bash
username:~/workspace/sep (master) $ git reset HEAD sep-11
Unstaged changes after reset:
M       sep-11
```

| Staging area before |Staging area after |
|:------------------------:|:-----------------------:|
|sep-11 (tracked|_no file is being tracked_ |

---
`git reset --soft HEAD~1`: Undo the commit  

git log before `git reset --soft HEAD~1`

```
commit 4280e5e3b91be31c1524333b0538fbbe88153fb1 (HEAD -> master, origin/master)
Author: User <weiz9762@hstat.org>
Date:   Sun Oct 15 17:59:31 2017 +0000

    change header size to #1
    
 commit 38387d4a6e6fe871e28fb1cca6cdabebe9dacdc1
Author: User <weiz9762@hstat.org>
Date:   Sun Oct 15 17:58:27 2017 +0000

    add readme
```

git log after `git reset --soft HEAD~1`
```
commit 38387d4a6e6fe871e28fb1cca6cdabebe9dacdc1 (HEAD -> master)
Author: User <weiz9762@hstat.org>
Date:   Sun Oct 15 17:58:27 2017 +0000

    add readme
```
---
`git reset HEAD~1`: single command that combine `git reset HEAD` and `git reset --soft HEAD~1` together, **it undo the commit and unstage the file**

`git reset --hard HEAD~1`: command that commbine all `git reset HEAD`, `git reset --sot HEAD~1` and `git checkout`, **it undo the commit, unstaged the added files and undo the changes in the file**

---
All the above commands will helps you "undo" the change that is not being push to the GitHub, and 
`git revert SHA` will Undo commit snapshot in GitHub by replace the new commit (undo the push)  


---
## Error Handling
`rm -rf .git`:

---
## Collaboration
`git clone`
fork:
