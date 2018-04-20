# VNC
Set VNC to start automatically
请按下面的步骤依次操作，就可以在树莓派开机时自动启用VNC
1. 打开终端窗口，复制并粘贴下面的命令：
sudo nano /etc/init.d/vncserver
2.在弹出的窗口中，将下面的代码复制并粘贴进去：

#!/bin/sh
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    $local_fs
# Required-Stop:     $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop vncserver
### END INIT INFO
 
# More details see:
# http://www.penguintutor.com/linux/vnc
 
### Customize this entry
# Set the USER variable to the name of the user to start vncserver under
export USER='pi'
### End customization required
 
eval cd ~$USER
 
case "$1" in
  start)
    # 启动命令行。此处自定义分辨率、控制台号码或其它参数。
    su $USER -c '/usr/bin/vncserver -depth 16 -geometry 1024x768 :1'
    echo "Starting VNC server for $USER "
    ;;
  stop)
    # 终止命令行。此处控制台号码与启动一致。
    su $USER -c '/usr/bin/vncserver -kill :1'
    echo "vncserver stopped"
    ;;
  *)
    echo "Usage: /etc/init.d/vncserver {start|stop}"
    exit 1
    ;;
esac
exit 0

