# setup-shell-ubuntu-16.4
Set up for ubuntu

#!/bin/sh
sudo apt-get update
# git
sudo apt-get install git -y
# cUrl
sudo apt-get install curl -y
# nvm node npm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
nvm install node && nvm use node

# yarn
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install --no-install-recommends yarn -y

# Atom
curl -L https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
sudo apt-get update && sudo apt-get install -y atom

# Chromium
sudo apt-get install chromium-browser -y

# Chrome
# wget -P /tmp/ https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
# sudo dpkg -i /tmp/google-chrome-stable_current_amd64.deb

# Mysql
sudo apt update && sudo apt install mysql-server -y

# MongoDB
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
sudo apt-get update && sudo apt-get install -y mongodb-org
sudo mkdir -p /data/db && sudo chown -R mongod:mongod /data/db
