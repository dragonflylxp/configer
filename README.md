#configer
#========
#
#python日志解析(C风格,支持注释)
#
#一.格式说明
#[]作为block分割符
#[.]作为二级目录，以此类推
#: 做为k,v分隔符
## 作为注释符，之后的内容全部忽略
#
#二.api
#1.load_conf:输入配置文件名，输出配置对象(重载字典)
#2.支持单例
#3.get支持foo/bar多级索引
#4.get出错抛异常
#5.支持热加载(单独线程监控)
#
#
#3.格式示例
##上下游服务模块配置
[Service]
#Testkey : Testval      这种不适用
[.svr_name1]
DefaultConnectTimeOut  :  1000
DefaultReadTimeOut  :  10000
DefaultWriteTimeOut  :  10000  #注释
DefaultMaxConnect  :  1000
DefaultRetry : 5
DefaultConnectType  :  LONG
DefaultLinger  :  0
SendBuf : 1000000
RecvBuf : 1000000
DefaultAsyncWaitingNum  : 100
IP : 127.0.0.1
Port : 9041

[.svr_name2]
DefaultConnectTimeOut  :  1000
DefaultReadTimeOut  :  10000
DefaultWriteTimeOut  :  10000  #注释
DefaultMaxConnect  :  1000
DefaultRetry : 5
DefaultConnectType  :  LONG
DefaultLinger  :  0
SendBuf : 1000000
RecvBuf : 1000000
DefaultAsyncWaitingNum  : 100
IP : 127.0.0.2
Port : 9041


#日志、pid等系统文件配置
[File]
#日志路径
log_dir : ./log/
#日志名称
log_name : phb.
#日志级别
log_level : 4
#保存pid的文件路径
pid_path : ./.phb.pid
#ip白名单路径
iplist_path : ./dict/iplist


#本地服务系统配置
[Local]
#服务名
_svr_phb_query_name : query
#启动服务的端口
_svr_phb_query_port : 7555
#服务的读超时(单位:ms)
_svr_phb_query_readtimeout : 400
#服务的写超时(单位:ms)
_svr_phb_query_writetimeout : 400
#服务启动的线程数
_svr_phb_query_threadnum : 12
#服务连接的类型(0:短连接, 1:长连接)example: 0 (use short connect)
_svr_phb_query_connecttype : 0
#服务使用的pool类型(0:XPOOL, 1:CPOOL, 2:EPOOL)
_svr_phb_query_servertype : 0
#CPOOL的socksize当使用CPOOL时设置有效
#[默认配置(uint),  _svr_se_query_quenesize : 100]
_svr_phb_query_quenesize : 1000
#CPOOL的socksize当使用CPOOL时设置有效
#[默认配置(uint),  _svr_se_query_socksize : 500]
_svr_phb_query_socksize : 2000

[Other]
key:value
