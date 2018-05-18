#OpenWallet

## 依赖库管理工具govendor

### 安装govendor

```shell

go get -u -v github.com/kardianos/govendor

```

### 使用govendor

```shell

#进入到项目目录
$ cd $GOPATH/OpenWallet

#初始化vendor目录
$ govendor init

#查看vendor目录
[root@CC54425A openwallet]# ls
commands  main.go  vendor

#将GOPATH中本工程使用到的依赖包自动移动到vendor目录中
#说明：如果本地GOPATH没有依赖包，先go get相应的依赖包
$ govendor add +external
或使用缩写： govendor add +e

#Go 1.6以上版本默认开启 GO15VENDOREXPERIMENT 环境变量，可忽略该步骤。
#通过设置环境变量 GO15VENDOREXPERIMENT=1 使用vendor文件夹构建文件。
#可以选择 export GO15VENDOREXPERIMENT=1 或 GO15VENDOREXPERIMENT=1 go build 执行编译
$ export GO15VENDOREXPERIMENT=1

```

## 源码编译跨平台工具

### 安装gox

```shell

$ go get github.com/mitchellh/gox
...
$ gox -h
...

```

### 编译wmd工具

```shell

# 进入目录
$ $GOPATH/OpenWallet/cmd/wmd

# 全部平台版本编译
$ gox

# 或自编译某个系统的版本
$ gox -osarch="linux/amd64"

```

## WMD工具使用

```shell

# -s <symbol> 是对某个币种的钱包发起操作

#执行初始化配置文件
$ ./wmd config init -s ada

#执行查看钱包管理工具的配置文件
$ ./wmd config see -s ada

#创建钱包
$ ./wmd wallet new -s ada

#执行批量创建地址命令
$ ./wmd wallet newaddr -s ada

#启动批量汇总监听器
$ ./wmd wallet startsum -s ada

```