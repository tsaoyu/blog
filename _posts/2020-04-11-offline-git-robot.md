---
layout: post
title:  "Offline Git for robots"
date:   2020-04-11 20:00:00
categories: [Random thoughts]
---
Have you struggled to find an internet connection in the field to update the code to the robot?
Have you painstakingly secure copy source code from the host machine to the robot?
Have you dreamed of one-click code deployment to your robot with just one click and no more mess on the version control?
This random thought is for you -- field roboticist -- who desperately need to update source code in the wild.
By using offline Git and custom VS code, you can send/receive code between your host computer and robot straight from your code editor.
It even allows a team of engineers working on the same code base seamlessly thanks to the git workflow.

I first use the offline Git for the sailing robot project that we often have to debug the code and update it near the sea.
It was not easy to give internet access to our raspberry pi. Traditional method using `rsync` is dangerous when many team members are working on the same code base. So we came up with the idea of using the Git offline and the script works pretty well during the last few years.
Since then I have thought of some one-click method to push/pull code to the robot. 
It turns out pretty easy to integrate the script in the VS code UI and I have been using this for my underwater robotics research at the University of Edinburgh so many times. So I decided to write a short article to share this with you.



## Offline Git 

Git is not just GitHub. As a socialised version of Git, GitHub gained a lot of attention due to the wide community behind it. 
But Git does not always require the internet connection to use. It is completely viable to use Git without the internet.
The core idea of Git is a distributed version control that works perfectly in this application. 
Instead of submitting code changes to the centralised GitHub, we share them offline through direct connection e.g. WiFi access point.
This will allow us to send/receive changes on the local network. Due to all changes are Git commits, it is error-prone to code overwrite and version conflict automatically. 


The first step is to set up an offline bareclone master on the robot. 
This can be done using the following script. You can copy the script to your host computer and change the username, host IP, git URL for your robot.

```bash
#!/bin/bash

# Set up the repository clones on a blank raspberry pi.
# Prepare the directories expected by push2pi and pullfrompi.
# This requires an internet connection to clone from Github.
# Running on host computer

ssh ${USER:=pi}@${ROBOT_IP:=192.168.2.2} <<'ENDSSH'
git clone git@github.com:yourusername/REPO_NAME.git REPO_NAME
git clone --bare REPO_NAME REPO_NAME-bare
cd REPO_NAME
git remote add bareclone ~/REPO_NAME-bare
ENDSSH
```
Two folders are created on the robot, one is the main working folder `REPO_NAME` and another is the bare clone `REPO_NAME-bare`.
Whenever you push/pull in your working folder all the changes are mirrored to the bare clone folder as well.
You don't have to do this manually when you update your code, the following scripts did the push and pull for you.


Push script simply SSH into your robot, push changes to the bare clone folder and update your working folder.

```bash
#!/bin/bash

# Running on host computer

set -e

echo "Pushing to the robot at ${ROBOT_IP:=192.168.2.2}..."
git push ${USER:=pi}@$ROBOT_IP:REPO_NAME-bare


echo "Pulling from bareclone on the robot..."
ssh $USER@$ROBOT_IP 'cd ~/REPO_NAME; git pull bareclone master'
```

Pull script, on the contrary, pull changes from the bare clone folder.

```bash
#!/bin/bash
# Running on host computer

set -e

echo "On ${ROBOT_IP:=192.168.2.2}, pushing to bareclone..."
ssh ${USER:=pi}@$ROBOT_IP 'cd ~/REPO_NAME; git push bareclone master'

echo "Pulling from the pi..."
git pull $$USER@$ROBOT_IP:REPO_NAME-bare master


```
Those three scripts altogether are what you need to use Git offline. I often run the first script in my bash to set up the repository and save the second one as `push2robot.sh` to reuse it. Similarly, the third script is useful when there are more yourself committing code to the robot and I call it `pullfromrobot.sh`. 

From now on, you should able to stick with your normal git workflow and push/pull to your robot without internet access.
The next section describes how to automate the push/pull in the code editor.



## VS Code custom buttom

Most time I use the code editor to commit/push code to my repository by a few simple clicks. I would also like to do this without leaving my text editor.
In VS code, it is pretty simple to custom the action using the action buttons plugin. 
The plugin is available at [here](https://github.com/SeunLanLege/vscode-action-buttons) in VScode extensions store.
After installing the plugin, the action button is ready for our custom script.
Add the following to your settings under `.vscode/ setting.json`

```json
"actionButtons": {
        "defaultColor": "#FFFFFF", // Can also use string color names.
        "loadNpmCommands":false, // Disables automatic generation of actions for npm commands.
        "reloadButton":"♻️", // Custom reload button text or icon (default ↻). null value enables automatic reload on configuration change
        "commands": [
            {
                "cwd": "/home/nelson/ORCA_control/utilities",     // Terminal initial folder ${workspaceFolder} and os user home as defaults
                "name": "Send to 🤖",
                "singleInstance": true,
                "command": "./push2robot.bash", // This is executed in the terminal.
            }
            {
                "cwd": "/home/nelson/ORCA_control/utilities",     // Terminal initial folder ${workspaceFolder} and os user home as defaults
                "name": "Pull from 🤖",
                "singleInstance": true,
                "command": "./pullfromrobot.bash", // This is executed in the terminal.
            }

        ]
    }
```
and hit the refresh button the `Send to 🤖` command will appear at the status bar. 
After committing your changes, you can click this button and the code will be automatically uploaded to the robot.
It is a good idea to `Pull from 🤖` first if you working as a team.
Git will try to merge the changes made by your teammates and keep you updated while offline. Sweet.

{% fullwidth  'assets/img/offline-git/action-button.png' 'Send to robot button in action'%}


## Best practise

The pull and push mechanism is very simple. But there are some common gotchas that not as intuitive as `rsync` or `scp` based method.
First of all, you always have to pull before push to your robot if your teammates are working on this repository together.
Unless you know what you are doing do not force push your changes to the robot.
Even it is an offline git, the principles of git workflow still apply.

This workflow also discourages the direct changes in your robot working directory e.g. `SSH` into the robot and `vi` on the source code.
You may able to commit them on the robot by using a separated robot account but it is harder to know who made those changes.
It is also harder to deal with merge on the robot when the file is modified at the same time. 

So the best practise of working with offline Git is to treat it exactly as online Git. Enjoy the full power of Git without thinking about the internet connection in the field. 

Enjoy hacking with offline Git.

