# Qingcloud-Docker-Hub 使用说明

## 创建镜像仓库用户
想要使用容器镜像仓库必须先创建一个用户，这个用户与IaaS用户无关。在创建的对话框中，填写用户名与密码即可。
![](img/create_user.png)

## 创建命名空间
所有的镜像仓库都是属于某个命名空间的，因此在使用（创建）镜像仓库前，必须先创建一个命名空间。在创建的对话框中，填写命名空间的名字，并选择访问权限，公开表示所有用户都可以pull这个命名空间下的任何仓库(但是只有添加过push权限的用户才能push），私有表示只有在当前命名空间下添加过权限的用户才可以访问(pull或者push)。
![](img/create_namespace.png)

### 添加权限
接下来我们要为命名空间添加访问权限，点击添加授权，选择镜像仓库用户以及要赋予它的权限Pull+Push或者Pull。
![](img/add_access.png)

## 创建仓库
有两种方式可以创建仓库：通过Web页面或者Docker client。

### 通过Web页面创建仓库
在创建镜像仓库的对话框中，选择镜像仓库创建到哪个命名空间下，并填入仓库的名称即可。
![](img/create_repo.png)

### 通过Docker client创建仓库
先使用已经存在的并且拥有相应命名空间push权限的镜像仓库用户登陆:
```docker login -u [username] -p [password] https://dockerhub.qingcloud.com```

然后通过```docker push```命令上传镜像仓库，即可成功创建仓库，并且在Web界面中观察到。
