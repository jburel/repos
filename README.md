# repos
A super-module of all the repositories in use

## Setup

For all repositories, you will want to add an "upstream" remote which
contains the source branch that you are looking to release. Where
upstream and origin are the same, you will likely want *both*.

## Release steps

### Initial setup

    git submodule init
    git submodule update

### Checkout the associated branches

    git submodule foreach git fetch upstream
    cd openmicroscopy/
    git checkout upstream/metadata52
    # etc. for all repos
    git commit -a -m "Updating all repos for 0.0.6""

### Tag and push all subcomponents

    # edit tag.sh to match your commit message
    git submodule foreach $PWD/tag.sh

### Tag an push the super repository

    cd ..
    git tag -s -m "Tag 0.0.6 - mid-summer version" 0.0.6
    git push origin 0.0.6
