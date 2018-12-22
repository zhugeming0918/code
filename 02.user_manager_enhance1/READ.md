
# 实现用户管理功能

## Demond:<br>
### 实现一个用户管理系统，可以与管理员用户进行交互，根据用户输入的指令(增删改查)，可以进行相应的操作：<br>
* 初次登录系统，提示用户输入管理员密码，提示用户当前系统无数据<br>
* 再次登录系统时，验证密码是否正确，三次输入错误后，必须等待三分钟后方可继续登录，登录成功后加载上次退出时保存的系统配置、用户数据<br>
* 等待用户输入命令，并进入该命令模式，（如输入add命令，后就会进入add命令模式，添加完依次数据后，可以无须再输入add，而直接输入数据实现添加，）<br>
* 进入命令模式后，就会进入输入数据阶段，检测数据源是否符合规范，符合规范就根据该命令来执行操作；若输入的数据为q!，则退出当前命令模式，重新要求用户输入命令。
### 命名模式详细信息：<br>
#### 命令模式：
* load:   加载用户数据，由用户指定导入文件位置（注意文件需以.json结尾,请谨慎操作）
* add:    添加用户信息，添加单个用户信息使用冒号隔开(用户名:年龄:联系方式)，一次添加多个用户使用逗号隔开
* update: 更新用户信息，更新单个用户信息使用冒号隔开(用户名:年龄:联系方式),一次更新多个用户使用逗号隔开
* delete: 删除用户信息，输入用户名，回显详细信息，提示是否确认删除；一次删除多个用户可以使用逗号隔开
* find:   查找用户信息，输入用户名，显示匹配的用户信息；一次查找多个用户可以使用逗号隔开
* list:   打印用户信息,输入排序关键字即是否升序，以冒号隔开，关键字不输入或不存在即默认用户名排序；y表示升序，缺省或其他任意字符表示默认降序（如输入:y）
* help:   查看命令帮组信息
* exit:   退出管理系统，并保存到指定位置
#### 输入数据阶段：
* 其他字符：判断字符是否合法，若合法，则送给命令执行
* q!:     退出当前命令模式，提示用户输入命令后进入该命令模式
<br>
增加管理员验证功能(即首次运行系统时候，提示管理员设置密码，用户进行 add list delete update find的时候需要验证管理员密码)