						Znginx使用指南

一、znginx 介绍
Znginx 是一款基于zabbix对Nginx监控的一个模板
Znginx 需要Nginx ngx_http_stub_status_module支持
Znginx 对Nginx服务状态进行监控、并通过触发器报警
Znginx 对连接状态进行监控，并设置图表
Znginx 提供了zabbix监控插件文件


二、Installation znginx
CentOS7/zabbix3
sudo mkdir /etc/zabbix/libexec/
sudo cp znginx/znginx /etc/zabbix/libexec/
sudo cp znginx/userparameter_znginx.conf.sample /etc/zabbix/zabbix_agentd.d/userparameter_znginx.conf


三、Nginx 设置
编辑Nginx配置文件，开启Nginx status模块
location /status  {
        stub_status on;
        access_log off;
        #allow 127.0.0.1;允许哪个ip可以访问
        }


四、重启服务生效
sudo killall nginx
sudo /$nginx-root/sbin/nginx
sudo service zabbix-agent restart


五、zabbix server web 导入模板
配置---模板---导入
zbx_export_templates.xml
