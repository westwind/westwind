Grafana
===

Dependencies
---
- Golang ([latest stable](https://golang.org/dl/))
- git
- NodeJS LTS

Installation
---

``` bash
## System Upgrade
sudo apt update -y
sudo apt upgrade -y
sudo init 6

## Install node.js
sudo apt install nodejs
node -v  ## node -v should > 10.0 or 11.0

## Method of update node.js
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
sudo n latest
sudo apt install --reinstall nodejs-legacy
sudo n rm $(node -v| awk -F'v' '{print $2}')
sudo npm uninstall -g n

## Install golang
mkdir bin
cd bin/
wget https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz (--no-check-certificate)
tar -xvf go1.12.7.linux-amd64.tar.gz
rm -rf go1.12.7.linux-amd64.tar.gz
export PATH=~/bin/go/bin:$PATH
export GOPATH=`pwd`
go version

## Install gcc
sudo apt install gcc

## Install grafana
(git config --global http.sslVerify false)
go get github.com/grafana/grafana
cd src/github.com/grafana/grafana/
go run build.go setup
go run build.go build

## Install yarn
sudo apt install npm
export NODE_TLS_REJECT_UNAUTHORIZED=0
sudo npm install -g yarn
yarn config set "strict-ssl" false
yarn install --pure-lockfile
yarn start

## Lunch grafana-server
./bin/linux-amd64/grafana-server
```

