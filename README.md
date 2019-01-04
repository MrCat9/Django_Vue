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




## app  model  添加测试数据




### 新建app  goods, trade, user_operation

```
manage.py@MxShop > startapp user_operation
```

将 新建的app 添加到 F:\pycharm\···\MxShop\MxShop\settings.py 下的 INSTALLED_APPS




### 设计app的model

#### users app 的 models  F:\pycharm\···\MxShop\apps\users\models.py

#### goods app 的 models  F:\pycharm\···\MxShop\apps\goods\models.py

将 DjangoUeditor 拷贝到 extra_apps 下

将 DjangoUeditor 添加到 F:\pycharm\···\MxShop\MxShop\settings.py 下的 INSTALLED_APPS

#### trade app 的 models  F:\pycharm\···\MxShop\apps\trade\models.py

#### user_operation app 的 models  F:\pycharm\···\MxShop\apps\user_operation\models.py




### 用 makemigrations 和 migrate 建表

manage下

```
manage.py@djangotest > makemigrations  # 生成数据表的py文件

manage.py@djangotest > migrate  # 生成数据表

```

更改了models.py（数据模型）（数据库）后，要执行makemigrations和migrate




### xadmin




### 添加测试数据

#### 把goods的封面图放在 F:\pycharm\···\MxShop\media\goods\images 下 

（与 F:\pycharm\···\MxShop\apps\goods\models.py 中 class Goods(models.Model) 的 goods_front_image 设置的路径相同）

#### 把商品分类后的代表品牌的logo图片放在 F:\pycharm\···\MxShop\media\brands 下

（与 F:\pycharm\···\MxShop\apps\goods\models.py 中 class GoodsCategoryBrand(models.Model) 的 image 设置的路径相同）

#### 把测试数据放到 F:\pycharm\···\MxShop\db_tools\data 下 

F:\pycharm\···\MxShop\db_tools\data\category_data.py  分类数据

F:\pycharm\···\MxShop\db_tools\data\product_data.py  商品数据

#### 通过脚本将数据导入  （独立使用django的model）

F:\pycharm\···\MxShop\db_tools\import_category_data.py  导入分类数据

F:\pycharm\···\MxShop\db_tools\import_goods_data.py  导入商品数据

#### 配置图片或者文件类的数据的访问路径（文件夹）

在 F:\pycharm\···\MxShop\MxShop\settings.py 下

```python
MEDIA_URL = "/media/"
MEDIA_ROOT = os.path.join(BASE_DIR, "media")
```

在 F:\pycharm\···\MxShop\MxShop\urls.py 下

```python
    url(r'media/(?P<path>.*)$', serve, {'document_root': MEDIA_ROOT}),
```




## restful api 介绍

是一个标准，不是架构 

restful api 概念  http://www.ruanyifeng.com/blog/2011/09/restful.html

restful 实践  http://www.ruanyifeng.com/blog/2014/05/restful_api.html




## vue介绍  vue项目结构




