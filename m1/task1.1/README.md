# DevOps_online_Chernivtsi_2021Q2
****Devops**** is a set of methods that helps developers actively interact with system administrators.
It allows you to link and integrate workflows into each other.
#### Devops Goals
-   fast entry into the product market
-   less time to fix the product
-   faster product development and deployment

## Task 1
1. Create the account "karachko" on the "Github". Install "Git for Windows" (https://git-scm.com/download/win) 
2. Create the  new repo "DevOps_online_Chernivtsi_2021Q2" on the "Github"
3. Create the folder 
- mk task1.1
5. Open "Git Bash"  on your workstation and move to this folder (cd c:/Users/admin/task1.1)
- git config --global user.name "karachko"
- git config --global user.email karachkonatasha@ukr.net
7. Clone repo to your workstation on your workstation 
- git clone https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2.git
8. *Create empty readme.txt file*
- touch readme.txt
9. *Make init commit*
- git init
10. *Create develop branch and checkout on it.* 
- git checkout -b develop
11. *Create index.html empty file. Commit* 
- touch index.html 
- git add index.html 
- git commit -m "Add file to develop"

10. *Create branch with name “images”. Checkout on it. Add images folder with
some images inside it. Commit.*
- git checkout -b images
- mkdir images
- Add files( 0-04-0a-6decd25b097dbc48eddf0ad3537ea9314a5b20d1bd1be2bacac7c3b78b4e8c8d_62951ab.jpg  0-04-0537c2824fb2f941c06a8aa43c5e3fb6652fa156e868c8e1eb590dea42fb36b892_3f4a47b9.jpg) to the folder images
- git add images/\*.*
- git commit -m "Add files to images"
11. *Change your index.html. Add images source inside it. Commit.*
   In the index.html write this code
     ```<img src="images/0-04-0a-6decd25b097dbc48eddf0ad3537ea9314a5b20d1bd1be2bacac7c3b78b4e8c8d_62951ab.jpg"> <img src="images/0-04-05-37c2824fb2f941c06a8aa43c5e3fb6652fa156e868c8e1eb590dea42fb36b892_3f4a47b9.jpg">```
- git add index.html
- git commit -m "Change file index.html"
12. *Go back to develop branch.*
 git checkout develop
13. *Create branch with name “styles”. Checkout on it. Add styles folder with
styles source inside it. Commit*
- git checkout -b styles
- mkdir styles
Add the file style.css in folder styles
- git add styles/\*.*
- git commit -m "Add files to styles"
14. *Change your index.html. Commit.*
- git add index.html
- git commit -m "Change file index.html"
15. *Merge two new branches into develop using git merge command.*
- git checkout develop
- git merge images
- git merge styles
- The merge conflict appeared after execution of the command "git merge styles"
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
- git add index.html
- git commit -m "Change file index.html"
- git merge styles

16. *Merge develop into master.*
- git checkout -b master
- git merge develop
17. *Push all your changes with all your branches to origin (git push origin --all)*
- The error was appered ``` fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository. Please make sure you have the correct access rights and the repository exists.```
- Fix this error 
``` git remote add origin https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2.git ```
- git push origin --all
18. *Execute command “git reflog“ and save it content somewhere (not in
repository) with filename “task1.1_GIT.txt”.*
- git reflog >> task1.1_GIT.txt


	  
								 
