## iOS代码混淆之XHObfuscator工具
### QQ群:750020052
### V1.0版本发布(2019/12/13)

&ensp;&ensp;&ensp;&ensp;笔者从2015年开始从事iOS开发,经历了市场对iOS开发需求的高点和低点,也经历了苹果本身对审核的宽松和严苛,曾经历了一夜之间十几款App被4.3,也曾收获无数的2.1大礼包.由于笔者所在公司面向B端服务,这种被拒的现象仍在发生...

&ensp;&ensp;&ensp;&ensp;为了减少这类问题,笔者想到了代码混淆,如果能够将模板代码混淆,让苹果认为是两种代码就可以减少4.3的概率.于是,笔者利用全部的业余时间开发了专门针对iOS项目代码混淆的工具```XHObfuscator```.

&ensp;&ensp;&ensp;&ensp;```XHObfuscator```提供了简洁的操作界面:

![主页.jpg](https://upload-images.jianshu.io/upload_images/20083069-4fc315cd49bb9df9.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### ```主页功能介绍:```***[请仔细阅读以下内容]()***
**软件内置海量词汇(15W+),用户亦可设置```用户词库```,在混淆时会先随机选取```用户词库```内容,再随机选取内置词库进行补充;
目前功能```只支持OC版本```;```Swift```相关功能正在开发中**

>关于忽略路径: 请手动添加想要忽略的文件,文件夹(以英文逗号分隔)
>
>关于三方库: 
>
>软件默认会过滤以下三方库及以Pod方式集成的三方库;如果三方库不是以pod集成又不在默认列表中,请手动添加到忽略路径中
>
>AFNetworking,Bugly,JPush,Masonry,MJExtension,MJRefresh,Reachability,SVProgressHUD,
>ReactiveObjC,SDWebImage,UMeng,JCore,FMDB,AMap,GoogleMaps,GooglePlaces,YYKit,
>IQKeyboardManager,FDFullscreenPopGesture,MBProgressHUD,SDCycleScrollView,


* 属性混淆 :
	* 使用```设置```界面```属性混淆前缀```的内容混淆
	* 项目内集成了```系统全部的属性```,在混淆时会将系统属性全部过滤,自创建的与```系统同名的属性```也会被过滤
	* @synthesize标记的属性,在声明的位置和@synthesize标记的位置都会修改,在具体使用中不会修改,请在参照混淆日志在文件内全局替换
* 方法混淆 :
	* 使用```设置```界面```方法混淆前缀```的内容混淆,项目本身
	* 项目内集成了```系统全部的方法```,在混淆时会将系统方法全部过滤,自创建的与```系统同名的方法```也会被过滤
* 类名(文件名)混淆 :
	* 使用```设置```界面```类名混淆前缀```的内容混淆
	* 仅会修改与```文件名同名的类```
* 目录混淆 :
	* 使用```设置```界面```目录混淆前缀```的内容混淆
	* 不会修改与项目xcodeproj文件同级的项目同名文件夹
* 修改项目名称 :
	* 使用```设置```界面```项目名称修改```的内容修改项目名
	* 如果填写了```替换原有前缀```,修改项目时会将原有前缀替换为```设置中的前缀内容```
	* 会自动修改pch文件路径
	* 修改后请点击选择新的Scheme,如找不到,新建一个即可
* 删除注释
* 英文字符串加密
	* 对纯英文字符串进行硬编码加密,可设置加密等级:30%,60%,100%
	* 使用```设置```界面```字符串加密前缀```的内容加密
* 中文字符串加密
	* 对包含中文的字符串进行base64加密,可设置加密等级:30%,60%,100%
	* 使用```设置```界面```字符串加密前缀```的内容加密
* 敏感词过滤
	* 过滤项目中包含的黄赌毒等敏感词汇
* 修改图片资源hash值 : 
	* 翻新项目中图片hash值
* 修改图片资源名称 :
	* 使用```设置```界面```图片翻新前缀```的内容修改图片名
	* 仅会修改```asset```中的图片名称
* 添加垃圾类和垃圾代码 :
	* 会在项目根目录创建文件夹为```垃圾代码前缀```内容的同名文件夹,需要手动导入到项目中(也可以自动导入项目,但测试时发现间所需较长,遂暂时取消自动导入功能
	* 添加垃圾代码功能待添加)
* 翻新xcodeproj中文件ID :
	* 采用自创建文件ID,替换项目配置文件的ID
	* 关于Xcode默认的ID的生成规则,目前无资料可查,关于采用自创建规则的影响,仍不可知,介意请慎用
* 点击开始混淆,会顺序执行功能
* ```开始混淆前,需保证项目名,项目根目录,代码根目录的名称相同```
___

![设置.jpg](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA4MzA2OS03NDRmN2YyNDNlMmZiNzA1LmpwZw?x-oss-process=image/format,png)
#### ```用户设置界面:```
* 如图所示,混淆前对应功能需手动设置所需前缀,如对应功能没有设置,则默认为```XH```;```字符串加密```默认为```XHSTRING```
* 点击保存,相应配置会保存到服务器

___
![词库.jpg](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA4MzA2OS1kNzIzZjZkNDNkZTY5YmUwLmpwZw?x-oss-process=image/format,png)
#### ```用户词库界面:```
* 单词之间需以```英文逗号```分隔
* 点击提交后会上传到服务器

___

![生成套图.jpg](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA4MzA2OS01YjYzNTRlZjkyNjY1MTBlLmpwZw?x-oss-process=image/format,png)
#### ```生成套图界面:```
* 点击```选择icon```上方按钮,会打开文件选择器,选择需要添加的icon
* 为保证生成的图片的清晰度,```选择的icon尺寸最好大于等于1024```
* 点击```选择背景填充色```上方按钮,会打开调色板,选择需要的颜色
* 点击```导出套图>>>```会在桌面导出全部尺寸的```iPhone,iPad```的启动图标和启动图

___

![反馈建议.jpg](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA4MzA2OS1jZmQwYmM0NThhZTBjM2RlLmpwZw?x-oss-process=image/format,png)
#### ```反馈建议界面:```
* 在使用过程中,有任何问题,建议可在此处提交,笔者会及时处理

___

![QQ群.jpg](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA4MzA2OS1jYjBjMTRmNGUwOWQ3NWFiLmpwZw?x-oss-process=image/format,png)
#### ```QQ群:```
* 欢迎扫码加入群聊,在这里可以沟通上架遇到的问题,可以愉快的吹水,可以更及时的反馈问题和建议

___

#### 部分效果展示: ####
```中文加密前后对比```
![中文加密前后对比.jpg](https://upload-images.jianshu.io/upload_images/20083069-5c984411c4a1e86f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
___

```英文加密前后对比```
![英文加密前后对比.jpg](https://upload-images.jianshu.io/upload_images/20083069-1079d1ed18c2ed73.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
___

```类名混淆前后对比```
![类名混淆前后对比.jpg](https://upload-images.jianshu.io/upload_images/20083069-ee76c6c0d64757df.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
___

```目录混淆前后对比```
![目录混淆前后对比.jpg](https://upload-images.jianshu.io/upload_images/20083069-a6a85c849d6ba378.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
___

```垃圾类内容展示```
![垃圾类内容展示.jpg](https://upload-images.jianshu.io/upload_images/20083069-f485111eadc97284.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
___

```项目名混淆前后对比```
![项目名混淆前后对比.jpg](https://upload-images.jianshu.io/upload_images/20083069-198a4bfeae821bfe.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 软件下载地址
码云: https://gitee.com/XHStudio/XHObfuscator

Github: https://github.com/XHStudios/XHObfuscator


___

#### ```写在最后:```

### 本软件非专业iOS开发请慎用 ###

* 本软件可能会产生编译错误;在混淆前,请做好代码备份,```软件也会对项目进行Git仓库初始化```
* ```出现错误时,请参照混淆日志,在文件内或者项目全局进行替换```
* 如果项目已经创建Git,但```未commit```,软件```不会进行commit操作```,请知悉
* 此软件非免费开源软件,希望可以帮到您;笔者会持续进行版本迭代,每次升级的内容会在文章开头详细说明!
* 详情可入群私聊群主,感谢大家的支持!

### 安装时如果提示```软件已经损坏,无法打开```
* 打开终端（Terminal.app）
* 拷贝粘贴 sudo spctl --master-disable  ，按回车键
