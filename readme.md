### 【安裝環境】

1. [Hyper-V系列#1 - Hyper-V虛擬機安裝 (連Win10 Home家用版也可以安裝喔!)](https://www.youtube.com/watch?v=NDx-2iEPfnM)
2. [在 Windows 10 上安裝 WSL | Microsoft Docs](https://docs.microsoft.com/zh-tw/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)[在 Windows 10 上安裝 WSL | Microsoft Docs](https://docs.microsoft.com/zh-tw/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)
3. Docker Desktop [Docker Desktop for Mac and Windows | Docker](https://www.docker.com/products/docker-desktop)

### 【Docker Desktop介面】

- Containers / Apps 容器、真正運行的環境

- Images 映像檔

- Volumes 硬碟、資料夾...

- Dev Environments 參數設置

### 【VSCoder 插件】

- Remote Development
  
  - try a Development Container sample
  
  - Reopen in Container
    

### 【設定建置方式 dockerfile】

- images

- dockerfile

- dockerContainer

### 【設定檔案說明】

```javascript
// devcontainer.json

// For format details, see https://aka.ms/devcontainer.json. For config options, see the README at:
// https://github.com/microsoft/vscode-dev-containers/tree/v0.191.0/containers/javascript-node
{
  "name": "Node.js",
  "build": {
    //建置方式
    "dockerfile": "Dockerfile",
    // Update 'VARIANT' to pick a Node version: 12, 14, 16
    "args": { "VARIANT": "14" }
  },
  // Set *default* container specific settings.json values on container create.
  // 可以做vscode的設定
  "settings": {},
  // Add the IDs of extensions you want installed when the container is created.
  //預設使用外掛
  "extensions": [
    "dbaeumer.vscode-eslint"
  ],
  // forwardPorts 外外面連結的port設定，可以用本機測網頁
  // Use 'forwardPorts' to make a list of ports inside the container available locally.
  // "forwardPorts": [],
  // Use 'postCreateCommand' to run commands after the container is created.
  // "postCreateCommand": "yarn install",
  // postCreateCommand 起專案的時候會預先執行的指令
  // Comment out connect as root instead. More info: https://aka.ms/vscode-remote/containers/non-root.
  "remoteUser": "node"
}
```

```javascript
# Dockerfile

# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.191.0/containers/javascript-node/.devcontainer/base.Dockerfile
# [Choice] Node.js version: 16, 14, 12
ARG VARIANT="16-buster"
# images映像檔路徑 之後起專案會到這個路徑下載
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}
# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"
# [Optional] Uncomment if you want to install more global node modules
# RUN su node -c "npm install -g <your-package-list-here>"
```
