
# VNC
Set VNC to start automatically
请按下面的步骤依次操作，就可以在树莓派开机时自动启用VNC
1. 打开终端窗口，复制并粘贴下面的命令：
sudo nano /etc/init.d/vncserver
2.在弹出的窗口中，将code中的的代码复制并粘贴进去。（说明：code文件在VNC目录下找）

3.在键盘上同时敲Ctrl + X键，然后敲y键，保存并退出。

4.在终端窗口中，复制并粘贴下面的命令：
sudo chmod 755 /etc/init.d/vncserver

5.在终端窗口中，复制并粘贴下面的命令：
sudo update-rc.d vncserver defaults

