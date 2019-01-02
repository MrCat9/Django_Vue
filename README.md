# Django_Vue

摘自  https://coding.imooc.com/class/131.html




## 项目初始化




### 安装Vue项目的依赖包

cmd下，cd到vue项目目录

```
cnpm install
```




### 运行Vue项目

cmd下，cd到vue项目目录

```
cnpm run dev
```




### 创建虚拟环境

cmd下

```
mkvirtualenv -p C:\Users\···\AppData\Local\Programs\Python\Python36\python.exe VueShop
```




### 安装django（1.11）

cmd下

```
(VueShop) F:\pycharm\···\MxShop>pip install -i https://pypi.douban.com/simple django
```




### 安装 Django REST framework 

https://www.django-rest-framework.org/




### 新建django项目  MxShop

```
项目解释器选择虚拟环境VueShop下的python.exe

application name写users

不使用admin
```




### 修改django项目使用的数据库为MySQL

MxShop\MxShop\settings.py

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': "mxshop",
        'USER': 'root',
        'PASSWORD': "123456",
        'HOST': "127.0.0.1",
        'OPTIONS': { 'init_command': 'SET default_storage_engine=INNODB;' }
    }
}
```




### 新建数据库  mxshop




### 安装django的MySQL驱动  mysqlclient

cmd下

```
(VueShop) F:\pycharm\···\MxShop>pip install mysqlclient
```

mysqlclient安装过程中可能出错，可访问 https://www.lfd.uci.edu/~gohlke/pythonlibs/




### 安装图片处理的包 pillow

cmd下

```
(VueShop) F:\pycharm\···\MxShop>pip install -i https://pypi.douban.com/simple pillow
```




### 新建python package和directory

新建 python package, apps

新建 python package, extra_apps

新建 directory, media

新建 directory, db_tools




### 将apps和extra_apps    mark directory as sources root




### 将apps和extra_apps添加到根搜索路径下

F:\pycharm\···\MxShop\MxShop\settings.py

```python
sys.path.insert(0, BASE_DIR)
sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))
sys.path.insert(0, os.path.join(BASE_DIR, 'extra_apps'))
```




## 
