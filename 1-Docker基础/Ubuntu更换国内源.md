# Ubuntu 20.04系统更改apt源为阿里源

以阿里源为例

## 1、备份源文件

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak
```

## 2、查看版本代号

```
lsb_release -c
```

> 每个版本的代号是不一样的，比如：
>
> Ubuntu 18.04代号为：bionic
>
> Ubuntu 19.04代号为：disco
>
> Ubuntu 20.04代号为：focal
>
> 所以每个版本的修改方式稍微会有点区别

## 3、编辑sources.list文件

```
vim /etc/apt/sources.list
```

> sources.list里的每个条目都是有格式的：
>
> ```text
> deb http://site.example.com/debian distribution component1 component2 component3
> deb-src http://site.example.com/debian distribution component1 component2 component3
> ```

> 后面的几个参数是对软件包的分类（ubuntu下是main、restricted、universe、multiverse）。
> 格式如下：
>
> ```
> deb 源URL 版本代号 main restricted universe multiverse
> deb-sr 源URL 版本代号 main restricted universe multiverse
> ```

```
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
```

## 4、更新软件列表 和 软件包

```
# 更新软件列表
sudo apt-get update

# 更新软件包
sudo apt-get upgrade

echo $?
0
```

