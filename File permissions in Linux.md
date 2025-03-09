# File permissions in Linux

## Project description

Today, let’s work with an organization’s research team. The mission is to ensure users on this team are authorized with the appropriate permissions to help keep the system secure. 

The objective is to examine existing permissions on the file system and determine if the permissions match the authorization that should be given. If they do not match, I will need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

## File and directory details

First, I checked the permissions on files and directories (pic 1).  
Then I checked all files and directories, hidden or not (pic 2).   
I also checked only hidden files to get an eye on it (pic 3).

## Description of the permissions string

In the /home/researcher2/projects directory, there are 5 files with the following names and permissions: 

* project\_k.txt  
  * User \= read, write,   
  * Group \= read, write  
  * Other \= read, write  
* project\_m.txt  
  * User \= read, write  
  * Group \= read  
  * Other \= none  
* project\_r.txt  
  * User= read, write  
  * Group \= read, write  
  * Other \= read  
* project\_t.txt  
  * User \= read, write  
  * Group \= read, write  
  * Other \= read  
* .project\_x.txt  
  * User \= read, write  
  * Group \= write  
  * Other \= none


There is also one subdirectory inside the projects directory named drafts. The permissions on drafts are:

* User \= read, write, execute  
* Group \= execute  
* Other \= none

**Let’s deep dive into the 10-character string to better understand the permissions:**  
Let’s take 1 example\!  
drafts: d r w x \- \- x \- \- \-

- **The 1st character (“d”)** indicates drafts is a directory (an hyphen instead “\-” would have indicated a file)  
- **The 2nd, 3rd and 4th characters (r w x)** indicate the permission for the user researcher2 (owner of the file): “r” \= files in the directory can be read / “w” \= new files can be created in the directory / “x” \= user can enter into the directory and access files  
- **5th, 6th and 7th characters (\- \- x)** indicate the permission for the group research\_team: “\-” in 5th position indicates the group doesn’t have the right to read files from the directory /  “\-” in 6th position indicates the group doesn’t have the right to create new files in that directory /  “x” indicates the group can enter into the directory and access its files.   
- **8th, 9th and 10th characters (\- \- \-)** indicate the permission for the other users from the system. These 3 hyphens indicate they have no right to read the directory, add new files or enter and access directory’s files.

## Focus on file permissions

In this organization, other users should not have write access to any files. For that reason, I removed other users' permission to write from the file project\_k.txt. (pic 5\)

## Focus on file permissions on a hidden file

.project\_x.txt is a hidden file because it has been archived. No one should have the write permissions on it, so I removed it from user and group. (pic 6\)

## Focus on directory permissions

The files and directories in the projects directory belong to the researcher2 user, so he should be the only user allowed to access the drafts directory and its contents. Let's remove the group permission to access it\! (pic 7\)

## Summary

Permissions checked, I decided to change several of them in order to match the level of authorization the organization wanted. One final check above shows that I did it, using chmod commands to update permissions several times and  ls \-la each time to check the permissions status.