# Some-documents-for-us
某些东西，给我/我们自己看的
# pvzol战斗模块文档
## 如何加载
加载目前还没有制作，所以只能通过改包(记得签名)的方法修改。
## 包内目录
```
configure.json(必要)
SunBack.png(必要)
plug.json(必要)
background
  background1.jpg
plant
  SunFlower.gif
  Peashooteratt.gif
  Peashooter.gif
zombie
  Zombie.gif
  FlagZombieAttack.gif
等等等等
```
## plug.json
### camera
定义窗口视图。
   | 接口       | 类型   | 描述                   |
   |-------------|--------|-------------------------------|
   | weight        | int | 定义分辨率大小      |
### background
定义背景图。
|接口|类型|描述|
|--|--|--|
|background|double|游戏中，显示背景图片的长部分/整张图片的长
|png|String|背景图片的路径|
|left|double|显示部分中，植物网格左部外边距/显示部分的长|
|right|double|显示部分中，植物网格右部外边距/显示部分的长|
|top|double|显示部分中，植物网格顶部外边距/显示部分的宽|
|bottom|double|显示部分中，植物网格底部外边距/显示部分的宽|
|gX|int|植物网格横向格数|
|gY|int|植物网格纵向格数|
|latticeW|double|网格每格的长/显示部分的长|
|latticeH|double|网格每格的宽/显示部分的宽|

有可能各位有点懵，我画张图就行了。
### plant
在这里你需要这样子写：
```
"plant":{
    "0":{},
    "1":{},
    ……
}
```
这里的数字指植物id。<br>
补充一点:<br>
这里的所有距离都是以`一核长度/20`计算！<br>
这里的所有距离都是以`一核长度/20`计算！<br>
这里的所有距离都是以`一核长度/20`计算！<br>
#### 植物整体:
|接口|类型|描述|
|--|--|--|
|name|String|名称|
|health|int|血量|
|targetrang|Array|发现目标的范围。比如向正前方发射子弹的豌豆射手，[0,240]|
|loop|Object|是否使用循环播放贴图。如果写了这一条，gif部分必须有loop，否则就会出错。|
|gif|Object|定义植物的贴图。|
|catapult|Array|定义子弹。就算不发子弹，也要留着[]。|

#### 植物贴图
你需要这样写:
```
"gif":{
    "normal":{},
    "attack":{}
}
```
第一种方法:
|接口|类型|描述|
|--|--|--|
|gif|String|指定gif文件的路径。第一次放置/使用需要加载一段时间，可以使用预加载。|
|size|Array|如[20,20]，指定碰撞箱/贴图大小。|
|maxtime|double|gif播放一次的时间，以秒为单位。|
|loop|int|写不写取决于上面你有没有写loop。如果是播放一次就写1|

第二种方法:忘了，反正不常用。

#### 植物子弹
你需要这样写:
```
"catapult":[
    {},{},……
]
```
一个标准的子弹:
|接口|类型|描述|
|--|--|--|
