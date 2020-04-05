# About
This repo contains my solutions for MOOC course
`DevOps with Docker 2019`

## Organization
Excercies are organized into directories per Parts.
Each file contains required output for completion.

## Notes
Open Administrator Powershell to project folder:
cd F:\Documents\Opiskelu\DevOpsDocker2019

Remember to switch to a branch relevant to current project when commiting

SSH into a detached container (-d) with command:
`docker exec -it <container-id> bin/bash` OR
`docker exec -it <id> bash`

### Removing dangling Docker images
docker rmi $(docker images -f "dangling=true" -q)

### Volumes:bind mounting and EACCESS errors on windows
On Windows 10 (atleast on build 1809) while using powershell 5.\*
You need to bind working directory with command ${pwd}. Working command is

> docker run -v ${pwd}:/mydir youtube-dl https://imgur.com/JY5tHqr

For binds to single files you have to use absolute paths (in Windows)

> docker run -v F:\Documents\Opiskelu\DevOpsDocker2019\Part\_1\8\log.log:/usr/app/logs.txt devopsdockeruh/first\_volume\_exercise

You need to give Docker Engine access file sharing access to those disks
for that exercise to work. According to https://stackoverflow.com/a/59984239
access was silently given. Atleast on version 2.2.0.4 binding volume raises error

> Error response from daemon: status code not OK but 500: {"Message":"Unhandled exception: Access is denied. (Exception from HRESULT: 0x80070005 (E_ACCESSDENIED))"}. 

You need to enable access to disk(s) in Docker/Settings/Resources/File Sharing/

## Using windows standard user with Docker

You need to add your logon account to Windows group, docker-users. Docker for Window will create this group automatically when docker for Windows is installed.

Steps:

    Logon to Windows as Administrator
    Go to Windows Administrator Tools
    Look for Windows Computer Management and click on it.
    Or you can skip steps 1, right mouse clicking Computer Management, go to more, and select run as administrator and provide Administrator password.
    Double click docker-users group and add your account as member.
    Also add your account to Hyper-V Administrator. This was added when you installed docker for Windows.
    Log off from Windows and log back on.
    Click on Windows icon on bottom left and start Docker for Windows. This will start docker windows service.
    9 Start Windows Powershell and type docker --version. It will show Docker version 17.09.1-ce, build 19e2cf6. This is the latest version.

