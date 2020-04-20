# Scripts
Various scripts that I use in my environments.

[NodeJS](#nodejs) | [Releases](#releases) | [Publishing](#publishing)

## NodeJS
Setting up NodeJS on macOS using a simple script: [setup-nodejs.sh](https://github.com/mindreeper2420/documentation/blob/master/scripts/setup-nodejs.sh)

```bash
# ==========================================================================
# THIS SCRIPT ASSUMES THE USE OF GULP, WITH AN EXISTING GULP.JS AVAILABLE
#
# Setup script for installing project dependencies.
#
# NOTE: Run this script while in the project root directory.
#       It will not run correctly when run from another directory.
#       DO NOT RUN INSIDE OF THE SCRIPTS DIRECTORY
# ==========================================================================

# exit script on errors
set -e

# Set node directory for use in scripts
init(){
  NODE_DIR=node_modules

  echo 'Node directory set.' $NODE_DIR
  sleep 2
}

# Clean any existing project dependencies.
clean() {
  # Remove the node directory if it exists
  # and install dependencies from the package.json file.
  if [ -d $NODE_DIR ]; then
    echo 'Removing any existing project dependencies...'
    rm -rf $NODE_DIR
  fi
  echo 'All pre-existing project dependencies have been removed!'
  sleep 2
}

# Install project dependencies from the package.json file.
install(){
  echo 'Now installing project dependencies...one moment please'
  npm install
  sleep 2
}

# Build the project
build() {
  echo 'Running the build scripts now...'
  gulp deploy
  echo 'Build complete. Run gulp development or npm run development to start a local server.'
  sleep 2
}

init
clean
install
build
```

## Releases
Script for automatically updated the release numbers on GitHub: [release.sh](https://github.com/mindreeper2420/documentation/blob/master/scripts/release.sh)

```bash
# A basic script for updated the release on a GitHub repo
if [ "`git status -s`" ]
then
  echo "You have unstaged commits. Please commit any pending changes."
  exit 1;
fi

echo "Checkout Master branch"
git checkout master

echo "Pull latest from master"
git pull --rebase origin master

echo "Update NPM Version"
VERSION=${1?Error: delineate major, minor, patch or prerelease}
npm version "$VERSION"

echo "Update Changelog"
gren release -P --override && gren changelog --override

echo "Commit Changelog and push to master"
git add --all && git commit -m "Update Changelog"

echo "Push to Master"
git push origin master
```

## Publishing
Publishing the latest code changes to the designated GitHub Pages directory in your repo: [publish.sh\(https://github.com/mindreeper2420/documentation/blob/master/scripts/publish.sh)

```bash
# A basic script for publishing repository changes to a gh-pages branch
# This script assumes that you are using GitHub Pages and that you build your site using Gulp

echo "Checkout Master branch"
git checkout master

echo "Pull latest from master"
git pull --rebase origin master

echo "Build site"
gulp build

echo "Update subtee and push to gh-pages"
git subtree push --prefix _site origin gh-pages
```
