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

Permission Issues:
- `www-data` is the typical system user for Apache & Nginx web server - used for wordpress.
    - Need to `chown -R www-data:www-data .` or `chown -R www-data:www-data /var/www/html`
- To avoid FTP credentials (File System Issues) for plugin installation and media uploads, need to add this line to `wp-config.php`
```
define('FS_METHOD', 'direct');
```
- Troubleshooting File System issues besides FS_METHOD, is to set the volume bind with read/write permissions
```
version: "3.6"
services:
 wordpress:
   image: wordpress:latest
   container_name: wordpress
   volumes:
     - ../wordpress_public_html:/var/www/html:rw
```