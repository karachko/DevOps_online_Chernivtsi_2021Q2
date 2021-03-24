# DevOps_online_Chernivtsi_2021Q2
****Devops**** is a set of methods that helps developers actively interact with system administrators.
It allows you to link and integrate workflows into each other.
#### Devops Goals
-   fast entry into the product market
-   less time to fix the product
-   faster product development and deployment

## Task 1
1. I created the account "karachko" on the "Github" and installed "Git for Windows" (https://git-scm.com/download/win) 
2. I created the  new repo "DevOps_online_Chernivtsi_2021Q2" in the "Github"
3. I created Create the folder in the "Git Bush"
- mk task1.1
5. I opened "Git Bash"  in my workstation and moved to this folder (cd c:/Users/admin/task1.1)
- I configurated the variables in "Git Bash"
- git config --global user.name "karachko"
- git config --global user.email karachkonatasha@ukr.net
7. I cloned repo to my workstation
- git clone https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2.git
8. I created the empty readme.txt 
- touch readme.txt
9. I made git commit
- git init
10. I created the develop branch and checkouted on it.
- git checkout -b develop
11. I created index.html empty file and did Commit 
- touch index.html 
- git add index.html 
- git commit -m "Add file to develop"

10.I created branch with name “images” and checkouted on it. 
- git checkout -b images
- mkdir images
- I added images folder with some images inside itand did Commit*Add files( 0-04-0a-6decd25b097dbc48eddf0ad3537ea9314a5b20d1bd1be2bacac7c3b78b4e8c8d_62951ab.jpg  0-04-0537c2824fb2f941c06a8aa43c5e3fb6652fa156e868c8e1eb590dea42fb36b892_3f4a47b9.jpg) to the folder images
- git add images/\*.*
- git commit -m "Add files to images"
11. I changed my index.html and added images source inside it. I did Commit
   In the index.html I wrote this code
     ```<img src="images/0-04-0a-6decd25b097dbc48eddf0ad3537ea9314a5b20d1bd1be2bacac7c3b78b4e8c8d_62951ab.jpg"> <img src="images/0-04-05-37c2824fb2f941c06a8aa43c5e3fb6652fa156e868c8e1eb590dea42fb36b892_3f4a47b9.jpg">```
- git add index.html
- git commit -m "Change file index.html"
12. I went back to develop branch.
 git checkout develop
13. I created branch with name “styles” and checkouted on it. I added styles folder with
styles source inside it. I did Commit
- git checkout -b styles
- mkdir styles
I added the file style.css in folder styles
- git add styles/\*.*
- git commit -m "Add files to styles"
14. I chanded my index.html. I did Commit
- git add index.html
- git commit -m "Change file index.html"
15. I merged two new branches into develop using git merge command.
- git checkout develop
- git merge images
- git merge styles
- The merge conflict had been appeared after execution of the command "git merge styles"
```-$ git merge styles
"Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result."```
- Fix The merge conflict in file index.html
The merge conflict
```<<<<<<< HEAD

=======
<link rel="stylesheet" href="styles/style.css">
>>>>>>> styles
```
- I corrected the index.html
- git add index.html
- git commit -m "Change file index.html"
- git merge styles

16. I merged develop into master
- git checkout -b master
- git merge develop
17. I pushed all your changes with all your branches to origin (git push origin --all)*
- The error had been appered ``` fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository. Please make sure you have the correct access rights and the repository exists.```
- Fix this error 
``` git remote add origin https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2.git ```
- git push origin --all
18. I executed command “git reflog“ and saved it content somewhere (not in
repository) with filename “task1.1_GIT.txt”.*
- git reflog >> task1.1_GIT.txt


	  
								 
