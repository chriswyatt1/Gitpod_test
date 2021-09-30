# Gitpod 

Gitpod is a container-based dev platform that provisions ready-to-code environments in the cloud accessible through your browser.

Steps to run gitpod and explore the Nextflow training gitpod.

1. Install gitpod app: https://github.com/apps/gitpod-io/installations/new

2. Check out a github repo, by going to your github main page appending  https://gitpod.io/# to your     https://github.com/<github_username>/<my-repo>
Here gitpod will open an enviroment with all the files from within your git repo (this is like a git clone into the cloud).

You can also initiate a gitpod env from github, once you have installed the app (step 1). Then you can find this button in your github: ![image](https://user-images.githubusercontent.com/9978862/134880020-617e32c2-3de3-4a82-b950-3ec9d3fa3160.png)
  
3. Try opening the Nextflow training gitpod and check out its yml!
  
For Nextflow training check out : 
[https://gitpod.io/#https://github.com/chriswyatt1/Gitpod_test/](https://gitpod.io/#https://github.com/chriswyatt1/Gitpod_test/)

- Nextflow is installed and the tutorial data downloaded within the task commands of the .gitpod.yml.
  
The .gitpod.yml in the main git repo folder is the main config file to add software, download programs etc.

```
# List the start up tasks. Learn more https://www.gitpod.io/docs/config-start-tasks/
tasks:
  - name: Download Nextflow Tutorial
    init: |
      echo 'init script' # runs during prebuild
      echo 'start script'
      curl -s https://get.nextflow.io | bash
      mkdir /workspace/bin
      cp ./nextflow /workspace/bin/nextflow  
      export PATH=/workspace/bin:$PATH
      nextflow info
    command: echo 'Now Nextflow an the tutorial data are loaded'
```
  
In the above yml: 
**init** means prebuild scripts to run (such as downloading databases etc).
**command** execute once the workspace is open. In the above example I change some folders and permissions in the workspace.

4. Configure a prebuild.
To enable prebuilt workspaces for a GitHub repository, follow these steps:

- Go to the Gitpod GitHub app and click Configure
- Choose the organization or account you wish to install the Gitpod app for, then click Install
- You will be forwarded to Gitpod where you can confirm the installation
  
This will enable the prebuild so that when you open the gitpod again in this repo, it will load faster from the prebuild.

