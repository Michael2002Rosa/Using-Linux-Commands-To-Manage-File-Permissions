# 🔐 Linux File Permissions Management  
*A cybersecurity project demonstrating Linux commands to manage file permissions and authorization*

![Linux Permissions](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)
![Security](https://img.shields.io/badge/Security-228B22?style=for-the-badge&logo=securityscorecard&logoColor=white)

## 📝 Project Description  
Taking on the role of a security professional for a research organization, the team needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks: 
- Identified insecure permissions (e.g., world-writable files)  
- Restricted access to sensitive files and directories  
- Secured hidden archived files  

This demonstrates hands-on experience with **Linux authorization controls**, critical for protecting sensitive data.

---

## 🚀 Project Action  

### **Section 1: Checking file and directory details**
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system:

![alt text](https://i.imgur.com/Qw2tyXP.png)

We being by using ```cd``` to "change directory", meaning we change our working space to the directory specfified which is the projects folder. The command ```ls``` is used to list and the ```-l``` flag shows permissions. The addition of the "a" to create ```-la``` makes it so all files (including ones hidden) are displayed.


### **Section 2: Describing the permissions string**
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
* **1st character**: This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
* **2nd-4th characters**: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
* **5th-7th characters**: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
* **8th-10th characters**: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

Lets breakdown the following example from the previous output screenshot ```drwxr-xr-x 3 researcher2 research_team 4096 May 1 18:02 .```
Owner (researcher2) has:
* Full control (read/write/execute)

Group members(research_team) can:
* list contents, enter the directory, but cannot create/delete files,

Other users:
* have the same access as group members

### **Section 3: Changing file permissions on files and hidden files**
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined ```project_k.txt``` must have the write access removed for other:

![alt text](https://i.imgur.com/nd3z15p.png)

The ```chmod``` command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the ```project_k.txt``` file. After this, I used ```ls -la``` to review the updates I made.

The research team at my organization recently archived ```project_x.txt```. They do not want anyone to have write access to this project, but the user and group should have read access. 

The following code demonstrates how I used Linux commands to change the permissions:
![alt text](https://i.imgur.com/ct301i7.png)

I know ```.project_x.txt``` is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with ```u-w```. Then, I removed write permissions from the group with ```g-w```, and added read permissions to the group with ```g+r```

---

## 📜 License  
This project is part of the [Google Cybersecurity Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity).  

---

