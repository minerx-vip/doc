## 搭建中转服务器

## 1.一键脚本

TODO



## 2.分步教程

#### 2.1.安装依赖

```sh
if ! command -v redir >/dev/null 2>&1; then
    apt update
    apt install -y redir
fi
```



#### 2.2 配置

```sh
## 本地监听端口，一般跟 cport 保持一致即可
lport="17148"
## 将流量重定向到的远程端口
cport="17148"
## 将流量重定向到的远程地址
caddr="stratum-eu.rplant.xyz"

########################################################################
## 以上内容根据实际情况修改
## 以下内容不要修改
########################################################################
shell="readlink -f $(which redir) \
--loglevel=debug \
--lport=${lport} \
--cport=${cport} \
--caddr=${caddr}"
service_name="redir_${lport}"

## 注册为服务
## 准备配置文件
cat <<EOF > /etc/systemd/system/${service_name}.service
[Unit]
Description=${description}

[Service]
Restart=always
RestartSec=5
ExecStart=${bin_path}

[Install]
WantedBy=multi-user.target
EOF

## 启动并设置开机自动启动
systemctl daemon-reload
systemctl enable ${service_name}.service
systemctl stop ${service_name}.service
systemctl start ${service_name}.service

## 查看服务状态
## systemctl status ${service_name}.service

## 查看日志
journalctl -f -u ${service_name}.service
```

