# 命令
## 解压缩
1. .tar.gz压缩命令：tar -czvf  a.tar.gz  /路径
2. 解压命令：tar -xzvf  a.tar.gz

## USB相关
1. lsusb命令：查看当前usb端口占用

## 常用
1. ps -ef|grep SEC  : SEC下正在运行的进程详情
2. uname -a：显示系统信息 -a全部显示
3. sudo systemctl **stop** SeWebSvrd
    >stop：停掉服务
    >enable：开机自启
    >disable：关闭开机自启
    >start：启动
4. netstat -anp|grep 17002：查看端口占用情况
5. ```su -/su/su root```出现鉴定故障后，可用```sudo su root```命令代替

## 文件属性
1. chattr +i：会使文件受保护，管理员也无法删除
2. chattr -i：去除保护
3. lsattr：查看文件属性

## 服务端更新
1. updata  D:/sharefile/DKSJ 文件夹
2. 服务端终端：cp -ruv /media/sf_sharefile/DKSJ/client/secuprint-client-amd64/opt/DYSJ /opt/
    | cp选项    | 说明    |
    | --- | --- |
    |  -R/r,-recursive   | 递归处理，将指定目录下的所有文件与子目录一并处理    |
    |  -u, -updata   |  使用这项参数后只会在源文件更改时间较目标文件较新时或是没有相应名的文件存在时，才会执行复制   |
    |   -v, -verbose  |   显示详细信息  |

## Cent7下交叉编译
命令：make -f makefile.mips64el 等