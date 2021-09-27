# Gitpod 

Gitpod is a container-based dev platform that provisions ready-to-code environments in the cloud accessible through your browser.

Steps to run gitpod.

1. Install gitpod app: https://github.com/apps/gitpod-io/installations/new

2. Create a .gitpod.yml in the main git repo folder to start controlling your enviroment, add software, download programs etc.

```
# List the start up tasks. Learn more https://www.gitpod.io/docs/config-start-tasks/
tasks:
  - name: Download Nextflow Tutorial
    init: |
      echo 'init script' # runs during prebuild
      echo 'start script'
      curl https://s3-eu-west-1.amazonaws.com/seqeralabs.com/public/nf-training.tar.gz | tar xvz 
      curl -s https://get.nextflow.io | bash
    command: |
      mkdir /workspace/bin
      cp ./nextflow /workspace/bin/nextflow  
      export PATH=/workspace/bin:$PATH
```
  
In the above yml: 
**init** means prebuild scripts to run (such as downloading databases etc).
**command** execute once the workspace is open. In the above example I change some folders and permissions in the workspace.

3. Configure a prebuild.
On GitHub
To enable prebuilt workspaces for a GitHub repository, follow these steps:

- Go to the Gitpod GitHub app and click Configure
- Choose the organization or account you wish to install the Gitpod app for, then click Install
- You will be forwarded to Gitpod where you can confirm the installation

4. Check out your github repo, by appending  https://gitpod.io/#     to your     https://github.com/<github_username>/<my-repo>
Here you can see the enviroment with all the files from within your git repo (this is like a git clone into the cloud).
I have had permissions issues here using the seqeralabs git repo, but if you are the owner of the repo, it should be straight forward.
  
You can also initiate a gitpod env from github, once you have installed the app (step 1). Then you can find this button in your github: ![image](https://user-images.githubusercontent.com/9978862/134880020-617e32c2-3de3-4a82-b950-3ec9d3fa3160.png)

  
5. Add your favorite VS Code themes and extensions
You have access to all Visual Studio Code extensions published under the vendor neutral Open VSX registry. Install one by clicking the Extensions icon in the left sidebar and enter your favorite theme or VS Code extension. Add Nextflow.
  
```
vscode:
  extensions:
    - svelte.svelte-vscode
    - bradlc.vscode-tailwindcss@0.6.11
    - https://example.com/abc/releases/extension-0.26.0.vsix
```
Changes you make in your workspace such as themes and extensions are synced automatically to other workspaces.  
  
  
For Nextflow training check out : 
gitpod.io/#https://github.com/chriswyatt1/Gitpod_test/

- Nextflow is installed and the tutorial data downloaded within the task commands of the .gitpod.yml.
