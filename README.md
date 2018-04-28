# documentation
## GIT
- Git is a version control system for tracking changes in computer files and coordinating
work on those files among multiple people.
- At its core, it’s a key-value pair of sha1 and its corresponding content blob.
  - SHA1 - 
![SHA1](https://github.com/matindi/documentation/blob/master/sha1.png)
  - Persistent - because the files are stored on the file system. 
  - Map - because it consists of a key value pair composed of : 
    - A blob of data. -- piece of content.(emphasize)
    - A SHA1 representation of that blob of data.	(https://en.wikipedia.org/wiki/SHA-1)
    
    | Key         | Value                                    |
    |-------------|------------------------------------------|
    | Hello World | 557db03de997c86a4a028e1ebd3a1ceb225be238 |
 - An object in git is a key value pair of SHA1 and their corresponding immutable blobs.Step 6 above shows us a the "hello world" object.
  There are 4 types of objects in git : 
  1. commit
  2. Tags
(add the photo/representation of the object on the file system)
1. `mkdir example` 
2. `cd example`
3. `git init`
4. `echo "Hello World" | git hash-object --stdin -w`
  - This will create a 'hello world' object that will be stored inside the hidden .git 
5. Run `ls -a` to view all folders and files in your directory. You should be able to see a hidden .git folder
6. `tree -a`
  - ![SHA1](https://github.com/matindi/documentation/blob/master/example1.png)
  - This commands helps you view all the files and folders contained in your current working directory.
  - As you can see, an object representation of "Hello World" is stored in the objects folder. The initial 2 letters of the hash are used as the folder name. While the rest of the letters in the has are used as the object's name.
  

1. `mkdir banks`
2. `cd banks`
3. `git init`
4. `echo "ANZ" > banks.txt`
5. `mkdir list`
8. `cd list`
9. `echo "webisite : https://www.anz.com.au/personal/" > anz.txt`
10. `cd ..`
11. `git add banks.txt`
 - `git add list/anz.txt`
12. `git commit -m "initial commit"`  
