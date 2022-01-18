# conda 使用教程(linux)

## 1.下载安装

### 1.1下载

所有版本镜像(清华大学开源镜像网站) : [https://mirrors.tuna.tsinghua...](https://link.segmentfault.com/?enc=sOblv4n99zC8NuiEk%2FDfkQ%3D%3D.Zc3zac%2BJqgsqx94LnwKdMVkImPEUEmqwfeRABka8uox6mTzaOYjOYKx4lR2KwH2iKigYzH%2BQL0GRsIAGkJP7bg%3D%3D)

从中选择合适版本的镜像下载.如 [Anaconda3-5.3.1-Linux-x86_64.sh](https://link.segmentfault.com/?enc=j9YJSYAXH%2Bhvxtpsx%2BHp4Q%3D%3D.9UzT6VaR3UBSJu7wf22CdNhs1YgKkO813aWejEpaezcpldFQ4Q5nnFqSwAh33FA9Iy8dbdp9fHb1YhVE6o3bMIPzC88ySb%2BzvJS3LqlRAfSo2NZw3AJ%2BDvqrUHKv3ZAw)

### 1.2安装

```mipsasm
$ sudo bash Anaconda3-5.3.1-Linux-x86_64.sh 
```

然后根据提示,进行安装

## 2.相关命令

### 2.1查看所有环境

```crystal
$ conda env list
$ conda info -e
```

以上两个命令均可

### 2.2创建一个新的虚拟环境

```routeros
$ conda create -n env_name python=3.6
```

指定Python的版本,否则是Python默认的版本

### 2.3激活虚拟环境

```applescript
$ conda activate env_name
$ source activate env_name        # linux
$ activate env_name        # windows
```

### 2.4退出虚拟环境

```shell
$ source deactivate        # linux
$ deactivate env_name        # windows
```

### 2.5删除虚拟环境

```cmake
$ conda remove -n yourEnvname --all      # 删除虚拟环境
$ conda remove --name $env_name  $package_name      # 删除环境中的某个package
```