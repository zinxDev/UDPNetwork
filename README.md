# UDPNetwork 基于Unity提供的UDP通信和同步服务
# API提供一下类的实现：

# 1.UDPServer服务器实现；

# 2.UDPClient实现；

# 3.可靠UDP实现；

# 4.可靠UDP消息互发机制的通讯实现；

# API介绍：

# 1.开启服务器
# 开启服务器使用UDPServer类，用法如下：
# UDPServer server = new UDPServer(serverName, ip, serverLocalPort, serverListenPort, syncThreadNum);
# 参数含义：
# serverName：服务器名字；ip：监听客户端的ip地址；serverLocalPort：服务器用于监听客户端连接的端口；serverListenPort：服务器用于监听客户端消息的端口；syncThreadNum：用于状态同步的线程数；

# 2.启动客户端
# UDPClient client = new UDPClient(clientName, localIp, clientLocalPort, serverHost, serverPort, syncThreadNum);
# 参数含义：
# clientName:客户端名字；localIp：客户端用于监听消息的ip地址；clientLocalPort：客户端用于监听消息的端口号；serverHost：服务器的地址；serverPort：服务器的端口（serverLocalPort）；syncThreadNum：用于状态同步的线程数；

# 3.同步的使用
# SynContainer类提供同步服务，用法如下：
# (1)服务器开启同步：SynContainer synContainer = new SynContainer(syncName, udpServer);
# 参数含义：
# syncName：同步的名字;
# udpServer:UDPServer对象；
# (2)客户端开启同步：SynContainer synContainer = new SynContainer(syncName, udpClient);
# 参数含义：
# syncName：同步的名字;
# udpClient:UDPClient对象；

# 4.可靠UDP消息收发
# 使用RpcItemSync类进行消息量化处理，用法：
# RpcItemSync item = new RpcItemSync(messageName, id, syncId, udpServer, argLen, (syncId, args) =>{});
# udpServer.Register(id, new INetworkSync[] { item });
# 然后，在服务器就可以发送和收到消息名字为messageName、id、syncId的消息，客户端注册消息与此类似；
