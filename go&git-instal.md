## 在 Centos 7上安装及更新 go & git
### git install

`sudo yum -y install  https://centos7.iuscommunity.org/ius-release.rpm`            
先建立库        

`sudo yum remove git*`           
删除旧版，再安装 新版           
`sudo yum -y install  git2u-all`             

~之后 yum update git~

### go install 

同样可以用`sudo yum remove go*`删除旧版

`yum install -y golang`  

`go version`

### wget 方式安装：

1）`wget https://dl.google.com/go/go1.13.3.linux-amd64.tar.gz`

2）`tar -zxf go1.13.3.linux-amd64.tar.gz -C /usr/local`

3）`vim /etc/profile` 

```
#golang env config
export GO111MODULE=on
export GOROOT=/usr/local/go 
export GOPATH=/home/gopath
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```
4）source /etc/profile

go version





