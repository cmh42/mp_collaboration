# Version Control

### Preliminaries

We will be using GPG authentification. 
The following instructions are for setting up GPG authentification on a Mac. Do a quick web search using the items to get instructions for other operating systems.

1. [Check for existing GPG keys](https://docs.github.com/en/authentication/managing-commit-signature-verification/checking-for-existing-gpg-keys)
2. [Generate a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
3. [Add the GPG key to your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)
4. [Associate an email with your GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/associating-an-email-with-your-gpg-key)


## Version control, Git and Github

These instructions are based on the following page: https://docs.github.com/en/get-started/using-git/about-git

### Example 
We will construct a repository called `mp_work` and perform various file and version control operations on it.  

The work here is based on the page: https://docs.github.com/en/get-started/using-git/about-git

#### Part 1: Start a new repository and publish it on GitHub

Start by creating a new repository on GitHub. (You need to create an account on Github first and then create a repository.  A suggested example of creating a repoistory is [Hello World](https://docs.github.com/en/get-started/start-your-journey/hello-world).) In the present example I created an empty repository 
called `mp_work`. You should not initialise the repostory with a README or other files... it should be empty, waiting for your code. 

Open a terminal (on your local device) and enter the following instructions line by line. 

```shell
# Create a new directory, and initialize it with git-specific functions
git init mp_work

# Change into the `mp_work` directory
cd my_work

# Create the first file in the project
touch README.md

# Create other files or copy other files from another directory (this is what I do here)
# After this there should be 7 files in the folder my_work
cp ../mp_work_old/*.* .

# Add all the files to the staging area (or individually with files names)
git add *

# Take a snapshot of the staging area with information message
git commit -m "Add all original files 010725"

# provide the path for the repository you created on github
git remote add origin git@github.com:cmh42/mp_work.git

# push changes to github
git push --set-upstream origin main

```

#### Part 2: Contribute to an existing repository on GitHub

For this example I have created a  repository on github called `mp_test` (with various files - in fact, for simplicity, the same files as 
those contained in `mp_work`). 

```shell
# Download the `mp_test` repository to your machine
git clone git@github.com:cmh42/mp_test.git

# Change into the `mp_test` directory
cd mp_test

# Create a new branch to store new changes
git branch charles-branch

# Make some changes. Here I just do a simple edit of the README file.
echo "# Test area" >> README.md

# Stage the changed file
git add README.md

# Take a snapshot of the staging area (anything that's been added)
git commit -m "README edit"

# Push changes to github
git push --set-upstream origin charles-branch
``` 

#### Part 3: Contribute to an existing branch of a repository on GitHub

For this example I will use  the repository `mp_test` from above which has a `main` branch and the `charles-branch` branch.


```shell
# Change into the `mp_test` directory
cd mp_test

# Update all remote tracking branches, including the currently checked out branch
git pull 

# Have a look at the branches (the active branch is in green)
git branch

# Change into the existing branch called `charles-branch`.
git checkout charles-branch

# Make changes, e.g. I add a new file here and add another line to README.md
touch new_file.md
echo "A story line..." >> README.md

# Stage the changed files
git add new_file.md README.md

# Take snapshot of the staging area
git commit -m "Created new_file and edited README"

# Push changes to github
git push
``` 
