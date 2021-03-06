# Ubuntu-commands-practice#2

* ### 打印出系统内核版本 N.N.NN, 须使用 grep

> `uname -r | grep -o -E "[0-9]*\.[0-9]*\.[0-9]"`

* ### 找出 access.log 文件中出现 ERROR 字样开头的行, 须打印出行号, 及该行的前一行.

> `grep -B 1 -n -E "^ERROR" access.log`

* ### 统计 log 文件夹下, 每一个 .log 文件中带 WARN 字样的行数.
> `grep -rn -E "WARN" ./log`

* ### 打印出本机所有的 IPv4 地址

> `ip a | grep -o 'inet [0-9.]*' | sed 's/inet //g'`

* ### 为网卡 eth0 添加一个 IP 地址 172.20.1.3/24, 然后删除它.

>`ip addr add 172.20.1.3/24 dev eth0`

>`ip addr del 172.20.1.3/24 dev eth0`

* ### 禁用网卡 eth0, 然后启用它.
>`ip link set eth0 down`

>`ip link set eth0 up`

* ### 创建符号链接文件 /usr/local/bin/vi , 指向 /usr/bin/vim .

>`ln -s /user/bin/vim /user/local/bin/vi`

* ### 分别向系统默认 DNS 服务器, 及 8.8.8.8, 查询 qq.com 域名的 IP 地址.
>`nslookup qq.com`

>`nslookup qq.com 8.8.8.8`

* ### 添加一个用户 guest, 要求使用 UID 2013, 不创建用户目录.

>`useradd guest -u 2013`

* ### 将用户 guest 添加到用户组 media, 然后从中删除.

>创建用户组 `groupadd media`

> 将用户添加到用户组`usermod -G media guest`

>将用户从组中移除`gpasswd -d guest media`

>删除用户 `useradd guest`

* ### ping 域名 qq.com 4 次, 并设置超时时间为 1秒.

>`ping -c 4 -w 1 www.qq.com`

* ### 打印出 firefox 进程的 ID, 及命令行参数, 然后结束进程
.
>`ps -lA | grep firefox | awk '{print $4,$14}' | xargs kill -9`

* ### 将文件 a.txt 内的所有 ubantu 字符改成 ubuntu 后另存为 b.txt .

>`sed 's/ubantu/ubuntu/g' a.txt > b.txt`

* ### 设置 10 分钟后自动关机.

>`shutdown -h 5`

* ### 切换 guest 用户并执行 id 命令.

>`su guest;id`

* ### 将目录 src/ 打包成 tar.bz2 文件, 然后解压到 /tmp/ 目录下.

>`tar -jcf s.tar.bz2 ./src`

>`tar -jxf s.tar.bz2 -C /tmp`

* ### 分别找出 CPU 和内存占用率最高的进程, 须显示出 CPU 和内存占用率, 进程名, ID 及命令行参数.

>`ps -aux | sort -k3nr | head -1 | awk '{printf("cpu:%.2f\%,mem:%.2f\%,PID:%s,command:%s\n",$3,$4,$2,$11)}'`

>`ps -aux | sort -k4nr | head -1 | awk '{printf("mem:%.2f\%,cpu:%.2f\%,PID:%s,command:%s\n",$4,$3,$2,$11)}'`

* ### 打印出本机系统内核版本及名称.

>`uname -sr`


* ### 统计文件夹 src/ 下面有多少个 py 文件, 包含子目录.

>`ls ./src |grep -E "*.py" |wc -l`

* ### 下载图片 http://example.net/bird.jpg 到 /tmp/web.jpg

>`wget  http://example.net/bird.jpg  /temp/web.jpg`
