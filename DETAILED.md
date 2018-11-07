## Before we start

* **Some of the terms and commands that will be used are described here**
* Remote repository is our VCS server (in this example GitHub).
* The terms remote repository and GitHub will be used interchangebly from now on.
* Local repository is the repository cloned from GitHub on our local machine.

* ``` git add <some_file> ``` is an action that will prepare the content  that will be commited and eventually pushed to the remote repository
* ``` git commit ``` is an action that records the changes to the repository
* ``` git push ``` is an action that pushes the locally recorded repository changes to the remote repository

* **Additional informational sources are provided below** 

* If you want further information on how to use git, you may find it [here](https://git-scm.com/docs)

* You could find what a pull request is [here](https://help.github.com/articles/about-pull-requests/)
* You could find how to create a pull request [here](https://help.github.com/articles/creating-a-pull-request/i)
* You could find how to merge your pull request [here](https://help.github.com/articles/merging-a-pull-request/)


## Below you will find the detailed process used to create this repository

- Create new repository in GitHub name ```packer_nginx64```

- Clone the new repository on the local machine 

```
git clone https://github.com/firedot/packer_nginx64.git
```

- Go to the directory where the repository is located

```
cd packer_nginx64
```

- Create new branch

```
git checkout -b "addPackerTemplate"
```

- Create packer template
```
touch template.json
```
- Create Ubuntu preseed file, located under ``` http/ ```

``` 
mkdir http
cd http/
touch preseed.cfg
```

- Fille preseed.cfg with required information

- Add all files needed for building a box with packer

```
git add template.json http/ scripts/
```
- Comit the files  to be pushed to GitHub

```
git commit -m "Added packer template, along with answer file and provisioning script"
```

- Push the files to GitHub

```
git push --set-upstream origin addPackerTemplate
```

- Go to GitHub
- Create a pull request
- Merge the pull request to master

- Checkout to the master branch on the local repository

```
git checkout master
```

- Pull the changes from GitHub to the master branch on the local machine

```
git pull origin master
```

- Create new branch

```
git checkout -b "addGitIgnore"
```
- Create ```.gitignore``` file, which will help us in ommiting directories, which are not meant for upload to our Remote repository
```
touch .gitignore
```
- To the ```.gitignore``` file add files or directories that should be ignoedr

```
./packer_cache/
./output-*/
.kitchen
```

- Add the ```.gitignore``` file, which will help us ommit directories, which are not meant for upload to our Remote repository

```
git add .gitignore
```

- Commit the files that should be pushed to GitHub

```
git commit -m "Added .gitignore file"
```

- Push the files to GitHub

```
git push --set-upstream origin addGitIgnore
```

- Go to GitHub and create a pull request
- Merge the pull request to the master branch on GitHub

- Go back to your local repo
- Checkout to the master branch

```
git checkout master
```

- Pull the changes from GitHub

```
git pull origin master
```

- Create a new branch

```
git checkout -b "addKitchenTests"
```

- Create  ```.kitchen.yml``` - the file used to configure  Kitchen for testing

```
touch .kitchen.yml
```

- Add the configuration for Kitchen

```
---
driver:
  name: vagrant

provisioner:
  name: shell

platforms:
  - name: vbox/nginxe4
    driver:
      box: nginx64

verifier:
  name: inspec

suites:
  - name: default
```
- Create the directory where the kitchen tests reside: 

```
mkdir -p test/integration/default/
```
- Go in the newly created directory

```
cd test/integration/default/
```

- Create a new file, in which test will be described

```
touch check_pkg.rb
```
- Write the test 

```
    describe package('nginx') do
  it { should be_installed }
end
```

- Add the files for commit 

```
git add .kitchen.yml test/ 
```

- Commit the files

```
git commit -m "Added kitchen testing"
```
- Push the files to the Remote repository

```
git push --set-upstream origin addKitchenTests
```
- Go to GitHub
- Create pull request
- Merge the pull request

- Go to the local repository
- Checkout to the master branch

```
git checkout master
```
- Pull the changes from GitHub to the master branch in the local repository

```
git pull origin master
```

- Create a new branch

```
git checkout -b "addDETAILED"
```

- Add this file

```
git add DETAILED.md
```

- Commit the changes

```
git commit -m "Added DETAILED.md"
```

- Push to GitHub

```
git push --set-upstream origin addDETAILED
```

- Go to GitHub
- Create pull request
- Merge 

- Go to the local repository
- Checkout to the master branch

```
git checkout master
```
- Pull the changes from GitHub to the local repository

```
git pull origin master
```
