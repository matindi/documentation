# GIT
- Git is a version control system for tracking changes in computer files and coordinating
work on those files among multiple people.
- At its core, it’s a key-value pair of sha1 and its corresponding content blob.
  - SHA1 - 
  
    ![SHA1](https://github.com/matindi/documentation/blob/master/sha1Photo.png)
  - Persistent - because the files are stored on the file system. 
  - Map - because it consists of a key value pair composed of : 
    - A blob of data. -- piece of content.(eg.text or a file)
    - A SHA1 representation of that blob of data.	(https://en.wikipedia.org/wiki/SHA-1)
    
    | Key         | Value                                    |
    |-------------|------------------------------------------|
    | Hello World | 557db03de997c86a4a028e1ebd3a1ceb225be238 |
 - An object in git is a key value pair of a SHA1 and their corresponding immutable blobs.
  There are 4 types of objects in git : 
    1. Blobs
    2. Trees
    3. Commits
    4. Annotated Tags
    - Objects are usually stored in the objects directory. The image below shows 5 objects. They could be either of the 4 types above.
    
![branches](https://github.com/matindi/documentation/blob/master/branch.png)

Lets create our own object using a simple blob.ie. piece of text. And view it by running the following commands on the terminal : 
1. `mkdir example` 
2. `cd example`
3. `git init`
4. `echo "Hello World" | git hash-object --stdin -w`
  - This will create a 'hello world' object that will be stored inside the hidden .git 
5. Run `ls -a` to view all folders and files in your directory. You should be able to see a hidden .git folder
6. `tree -a`
  - ![SHA1](https://github.com/matindi/documentation/blob/master/example1.png)
  - This commands helps you view all the files and folders contained in your current working directory.
  - As you can see, an object representation of "Hello World" is stored in the objects folder. The initial 2 letters of the hash are used as the folder name. While the rest of the letters in the hash are used as the object's name.
  
We can also create objects using files and directories and later view them by running the commands below :  
1. `mkdir banks`
2. `cd banks`
3. `git init`
4. `echo "ANZ" > banks.txt`
5. `mkdir list`
8. `cd list`
9. `echo "webisite : https://www.anz.com.au/personal/" > anz.txt`
10. `cd ..`
12. `git status`
 - The directory and files we just added are not being tracked.ie.they haven’t been stored by git. Git stores this information in a data structure called a repository
A git repository contains, among other things, the following:
 - A set of commit objects.(object: is a key value pair of SHA1 and their corresponding immutable blobs )
 - A set of references to commit objects, called heads.
 - To commit our object(the files and directory we just created) to the git repository we have to stage the changes we’ve made. ie.the bank.txt folder and the list directory together with all the files and directories it contains.
 - The Git repository is stored in the same directory as the project itself, in a subdirectory called .git. 
 - There is only one .git directory, in the root directory of the project.
 - The repository is stored in files alongside the project. There is no central server repository.
11. `git add banks.txt`
 - `git add list/anz.txt`
   - This stages all the changes made to the entire directory before pushing them to the repository.If we run ‘git status’ again ,we get the following output : 
13. Running `git status` again, you'll be able to see that the new files have been staged.
12. `git commit -m "initial commit"`  
 - After multiple file and directory additions, the number of objects git will store will increase. 
## The object database
![object](https://github.com/matindi/documentation/blob/master/banks.png)

 - NB : The text in brackets below refers to objects. 
 - In the image above, we can start with (1177). Our first commit be4d points to the root of our project. 
 - Commit (bed4) then then contains the list directory and the banks.txt file.
 - Bank.txt then contains text ie. Anz(2399) while the directory/tree list, contains anz.txt(3ee7)
 - Anz.txt contains some text(361a)

## Branches
A branch in git is a pointer to a commit.

![branch](https://github.com/matindi/documentation/blob/master/finalBranch1.png)

A head is a pointer to our current branch.
1. Run `git branch`. - This should output master. The master branch is our current branch
 - The list of branches is stored in the `.git/refs/heads` directory.
2. Run `cat .git/refs/heads/master `
 - The output will be `ecd06be7b154715d762aaddf1241f580c6d6339d`. As noted earlier, a branch is a pointer to a commit and our   master branch currently points to the commit above.
 
