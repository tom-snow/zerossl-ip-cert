## 准备
1. 有公网 ip 的服务器(域名可选)
2. 安装有 nginx ( Windows 服务器推荐用 caddy )


## 使用说明
1. 前往 [Release](https://github.com/tinkernels/zerossl-ip-cert/releases) 下载最新版本的二进制文件
2. 解压到服务器上（可能需要 `chmod +x` 添加执行权限，推荐将此二进制文件保存到 ~/.local/bin 下，添加到 $PATH 环境变量内)
3. 下载 [配置文件](https://raw.githubusercontent.com/tinkernels/zerossl-ip-cert/master/exec/sample-config.yaml) 并修改（可参考本仓库内相应文件内的注释说明）
4. 下载并根据自己的 nginx 配置目录修改这两个 hook 文件，并在上面的配置文件中修改好 hook 文件的路径（Windows 下载cmd后缀的两个） [验证域名/ip时的 hook 脚本(重要),推荐使用本仓库修改过的文件](https://raw.githubusercontent.com/tinkernels/zerossl-ip-cert/master/exec/sample-nginx-verify-hook.sh)， [获取到证书后的hook操作脚本](https://raw.githubusercontent.com/tinkernels/zerossl-ip-cert/master/exec/sample-nginx-post-hook.sh)
5. 运行 `zerossl-ip-cert -config <这里填配置文件目录>` 来获取证书
6. 成功后运行 `crontab -e` 然后将 `12 3 * * * /path/to/zerossl-ip-cert -config <这里填配置文件目录> -renew` 填入，即可自动刷新证书

。
