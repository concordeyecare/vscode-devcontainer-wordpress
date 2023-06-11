# vscode-devcontainer-wordpress
Wordpress + MariaDB &amp; phpmyadmin (mysql) in vscode devcontainer.

Using docker with vscode devcontainer for local wordpress development environment.

Based off Automattic's writeup by Cameron Pavey: https://developer.wordpress.com/2022/11/14/seetup-local-development-environment-for-wordpress/

Setup Used:
- Windows 10
- Docker Desktop + WSL2 enabled
- VS Code Extension(s): 
    - `ms-vscode-remote.vscode-remote-extensionpack`
    - `ms-vscode-remote.remote-wsl`
    - `ms-vscode-remote.remote-containers`

Instructions:
1. VSCode: Ctrl + Shift + P (Command Palette)
2. Select `Dev Containers: Rebuild Without Cache and Reopen in Container`
3. [Optional] Click on prompt: `Starting Dev Container (show log)`

Important Notes:
- Wordpress available on port 8080: http://localhost:8080
- phpmyadmin available on port 8180: http://localhost:8180 