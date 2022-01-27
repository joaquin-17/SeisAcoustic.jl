<a name="logo"/>
<div align="center">
<a href="http://saig.physics.ualberta.ca/" target="_blank">
<img src="https://saig.physics.ualberta.ca/lib/tpl/dokuwiki/images/logo.png" alt="SAIG Logo" width="240" height="106"></img>
</a>
</div>

## Contributing to Seis packages

[![Generic badge](https://img.shields.io/badge/STATUS-WIP-<COLOR>.svg)](https://shields.io/)



This is a tutorial on how to contribute to the SeismicJulia project through Git & GitHub. Get familiar with Git and GitHub by following [this](https://drive.google.com/drive/u/0/folders/1nYoplIPSnvOUKFsexxTLJEUfWLfTTI02) page. Here we show how to create a GitHub account and fork a repo to your machine.  Then, we describe how to contribute to a public GitHub repo. Try to follow along even if you already have a Github account.

1. Go to github.com and create a GitHub account (“yourAccount”).
2. Go to the GitHub repo [SeisMain](https://github.com/SeismicJulia/SeisMain.jl) and fork the repository into your account by clicking the “Fork” button.
3. In your local machine, create the new directory that will contain the project
    ```console
    $ mkdir SeisMain
    ```
4. Config your username and email in your local machine. Use the same email account as in the GitHub account
    
    ```console
    $ git config −−globaluser.name "username"
    $ git config −−globaluser.email "email@example.com"
    ```

5. Go to the new directory and clone the repository you have forked in step 1 into your local machine:
    ```console
    $ cd SeisMain
    $ git clone https://github.com/yourAccount/SeisMain.jl.git
    ```
6. Check that the repo content is in your machine
    ```console
    $ cd SeisMain
    $ ls −la
    ```
7. Check the link between your machine and your repository in GitHub.
    ```console
    $ git remote −v
    $ origin https://github.com/yourAccount/SeisMain.jl.git (fetch)
    $ origin https://github.com/yourAccount/SeisMain.jl.git (push)
    ```

8. To keep your repository updated with the upstream, you need to sync both repos. Configure a remote that points to the upstream repository:
   ```console
   $ git remote add upstream https://github.com/SeismicJulia/SeisMain.jl.git
   ```
9. You can verify the new upstream repository you have specified typing
    ```console
    $ git remote −v
    $ origin https://github.com/yourAccount/SeisMain.jl.git (fetch)
    $ origin https://github.com/yourAccount/SeisMain.jl.git (push)
    $ upstream https://github.com/SeismicJulia/SeisMain.jl.git (fetch)
    $ upstream https://github.com/SeismicJulia/SeisMain.jl.git (push)
    ```

Now, you can
    
 - Fetch the branches and their respective commits from the upstream repository, and then merge the changes from upstream/master into your local master branch, in two separate steps:
    ```console 
    $ git fetch upstream
    ```
    or 
    ```console
    $ git merge upstream / master
    ```
    This brings your fork’s master branch into sync with the upstream repository, without losing your local changes.
If there are merge conflicts in your files when merging, you need to solve them (See [this tutorial](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/) on how to
solve merge conflicts from the command line).
 - Update your repo in one step:
    ```console
    $ git pull upstream master
    ```
    Careful: this action destroys the changes in your local repository in favor of the content in the upstream repo.
The git pull command is a combination of fetch and merge.

- Push the changes to your own remote repository:
    ```console
    $ git push −u origin master
    ```
    This will “upload” the changes to the remote repository origin. Here -u is used to remember the parameters origin (remote repository name) and master (local branch name).

As a summary, the first steps update your local version of a project from the upstream repo (SeismicJulia in our case), and then pushes the changes to your github account on the website’s server (yourAccount).

### Commit your contribution

Once your local directory, your personal repo and the upstream repo are all synced, you can start working on new contributions to the project. It is recommended that you work on specific features of the packages on a new branch in your local folder. First, create and then change to that branch by
```console
$ git branch branchname
$ git checkout branchname
```
or do everything together
```console
$ git checkout -b branchname
```
Once your work in the branch is ready, you should merge the branch to the master
```console
$ git checkout master
$ git merge branchname
```

Careful: There might be conflicts. [Learn how to solve them](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/).

If you are not planning to use the branch in the future, delete it with
```console
$ git branch −d branchname
```
Now you are in the master branch of your local directory, and you are ready for the following steps.

1. When you finish working on some part of your project in your local directory, you need to show these changes in your GitHub repo. This is done in two steps. The first step records the changes to the repo, and the second one
updates it. These steps are called commit and push respectively. But before, you should let GitHub know which files you are tracking, specially if you created new files. To do so,
```console
$ git add −−all
$ git add -a
```
2. Now, you are ready to commit all your changes
```console
$ git commit −m  "message with the changes"
```
3. The final step to broadcast your local changes to the repo is the push
```console
$ git push
```
4. Now, your local directory and the GitHub repo are updated and you can pull your work to the main upstream repo (that is, SeismicJulia project, for example). To do so, follow the steps:
   1. Go to your repo on the GitHub webpage
   2. Click: New pull request
   3. Click: Create pull request
   4. Add a title and a message explaining your job
   5. Review the pull request
   6. Send the request

After sending the pull requests, the owners of the package will review the pull request and merge it with the main code.

This is the end of the tutorial.

Happy coding.