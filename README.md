# 玩转Raspberry PI

安装好树莓派要做的几件事情
 - sudo raspi-config
   ![](./docs/raspi-config.png =200x60)



### 树莓派开启VNC Server 服务端

```
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
    su $USER -c '/usr/bin/vncserver -depth 16 -geometry 1920x1080 :1'
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
```

