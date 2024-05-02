# dev-env : Dev environment dotfiles, install, and setup


## Setting up CLI dev environment from scratch

This repo is primarily for getting a new ec2 instance up and running efficently. Once onto aws, want to be able to get the environment moving quickly in an automated fashion. Will work for any command line environment, providing a minimal dev environemt to work in.

1. login to aws via command line, navigate to environment.

2. clone repository using HTTPS link:
`git clone https://github.com/CNuge/dev-env.git`

3. Set up environment.
Have a look in `setup.sh`, make sure all the config files being copied and the utils being called to facilitate installs match your desired. You can add more install scripts to utils, or more generic config files to be copied to home dir and enabled.

Run setup
```
setup.sh
```
Source your bash profile
```
#source ~/.bashrc
source ~/.bash_profile

```

4. install mambaforge

```
cd ~
bash mambaforge.sh
# where mambaforge.sh is the most up to date mamabaforge downloaded by the setup command
# re-source following install
source ~/.bash_profile
```

4. 
install commitizen and precommit
```
conda install commitizen
conda install -c conda-forge pre-commit

```

4. Check `git-access` push/pull to/from github
- use personal access token instead of actual password when prompted.
 https://github.com/settings/tokens

5. Create a conda environment named 'dev' to do development work in, the command below sets the environment up with snakemake. Navigate to this directory and load the pre-built dev environment with the following

```
 mamba env create -f dev_environment.yaml 
```

conversely you can make a skeleton snakemake env with the following:
```
conda create -c bioconda -c conda-forge -n dev snakemake
```

6. Activate the conda environment 

```
conda activate dev
```

7. Clone and/or naviagte to the repository you are working with.

Can create a repo-specific conda env, or proceed with the global one. You can now begin work in the environment.


8. Working with R.

A conda environment with a large set of packages that may be required can be created from the yaml file included in this repository like so: 
```
conda env create -n r-dev --file r-dev.yaml
```



