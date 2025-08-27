安装：
目前能找到的一键安装脚本基本上都是不能用的，官方出了v2版本之后v1脚本就全部失效，这里我重新修改了之前大佬制作的脚本，在root用户下安装即可：

wget -N --no-check-certificate  https://raw.githubusercontent.com/serverspeed/caddy-v1/refs/heads/main/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh

如果需要卸载，则输入以下命令：

wget -N --no-check-certificate https://raw.githubusercontent.com/serverspeed/caddy-v1/refs/heads/main/caddy_install.sh && bash caddy_install.sh uninstall

使用说明：

启动：/etc/init.d/caddy start

停止：/etc/init.d/caddy stop

重启：/etc/init.d/caddy restart

查看状态：/etc/init.d/caddy status

查看Caddy启动日志：tail -f /tmp/caddy.log

安装目录：/usr/local/caddyCaddy

配置文件位置：/usr/local/caddy/CaddyfileCaddy

自动申请SSL证书位置：/.caddy/acme/acme-v01.api.letsencrypt.org/sites/xxx.xxx(域名)/

使用示例：

这里只做简单演示（复杂的还是用nginx吧），复制并修改好命令粘贴到shh，最后重启caddy即可：

echo "https://domain:443 {              #监听域名以及端口 

reverse_proxy example                   #反向代理 

root /usr/local/caddy/www/              #网站目录 

tls qq@qq.com                           #启用tls并自动申请ssl证书  

gzip                                    #启用gzip压缩

}" > /usr/local/caddy/Caddyfile         #写入到配置文件

/etc/init.d/caddy restart               #重启caddy

更多用法自行下载官方文档（为什么是下载呢，是因为官方把v1的内容全撤了，想看文档只能自己下载）：
https://caddyserver.com/caddy-v1-docs-archive.tar.gz
