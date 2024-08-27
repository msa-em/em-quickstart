# Elemental Microscopy Quickstart

This repository contains minimal configuration files to get started for an `Elemental Microscopy` article.

## People

This quickstart guide was developed by [Colin Ophus](mailto:cophus@gmail.com) and [Georgios Varnavides](mailto:gvarnavides@berkeley.edu). 

## Installation Instructions

### Edit locally and push changes

> [!WARNING]
> First, ask one of the organization members to give you `write` access to the forked repo.

> [!WARNING]
> In what follows and the configuration files, you will see references to `change-to-repo-name`, which you should replace with the repo name. E.g. this article would be `em-quickstart`.

Steps to edit locally:
- git clone repo (`git clone git@github.com:msa-em/change-to-repo-name.git`)
- switch to `dev` branch (`git checkout dev`)
- edit `environment.yml` to
  - change the environment `name` to the repo name
  - add your package dependencies, pinning versions as necessary
- create virtual environment (`conda env create -f environment.yml`)
  - you might need to remove the environment if it already exists (`conda remove -n change-to-repo-name --all`)
- activate virtual environment in two terminal windows (`conda activate change-to-repo-name`)
- edit `myst.yml` file by:
  - commenting these lines out
  ```yml
    jupyter: true
  ```
  - uncommenting these lines
  ```yml
  #  jupyter:
    #    server:
    #      url: 'http://localhost:8888'
    #      token: '512ac78f14e1141db1fac17e8b4099c1e5bc7d589518b38c'
  ```
- start the jupyter server in one of the terminal windows (`jupyter lab --IdentityProvider.token=512ac78f14e1141db1fac17e8b4099c1e5bc7d589518b38c --ServerApp.allow_origin='http://localhost:3000' --port=8888`)
- start MyST in the other terminal window (`myst start`)
- edit, commit, and push to `dev` as per usual
  - make sure **NOT** to commit your `must.yml` changes!
- open a draft pull request into `main` (if one doesn't already exist) and keep pushing your changes to `dev`
  - this will enable live previews and checks (see below)
  - when you're ready, merge pull request into `main`. Note this need to be "final" -- it's best practice to merge thematic content changes together

> [!NOTE]
> If you don't plan on editing the notebooks, you can skip the `myst.yml` and `jupyter lab` steps above

## Preview draft deployed site
The repo has two github actions to automatically deploy computational sites, for the following two case:
- Commits to `main` directly
- Pull requests into `main`

If you followed the instructions above (i.e. working off of `dev` and have an open pull request into `main`), then you should see a `github-actions` bot at the top of your pull request which will keep getting edited.
Simply click on the `Inspect` link to see the curvenote staging site, and press `preview` to see the deployed site based on your latest commit.

