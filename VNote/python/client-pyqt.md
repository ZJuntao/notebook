# client-pyqt
## 一、Socket
```python3
    socket.gethostname                                      #返回当前主机名
    s=socket.socket(socket.AF_INET, socket.SOCK_DGRAM)      #创建套接字
    s.getsocketname()[0]                                    #获取当前主机ip
```

## 二、知识点整理


### json库
```python3
    userParam = json.loads(retJson)
```
>- retJson：json字符串
>- json.dumps()函数是将一个Python数据类型列表进行json格式的编码（可以这么理解，json.dumps()函数是将字典转化为字符串）
>- json.loads()函数是将json格式数据转换为字典（可以这么理解，json.loads()函数是将字符串转化为字典）


## 三、python
### 1.bytearrary()函数（py）
**描述**
bytearray() 方法返回一个新字节数组。这个数组里的元素是可变的，并且每个元素的值范围: 0 <= x < 256。

**语法**
bytearray()方法语法：
```python3
    class bytearray([source[, encoding[, errors]]])
```

**参数**
* 如果 source 为整数，则返回一个长度为 source 的初始化数组；
* 如果 source 为字符串，则按照指定的 encoding 将字符串转换为字节序列；
* 如果 source 为可迭代类型，则元素必须为[0 ,255] 中的整数；
* 如果 source 为与 buffer 接口一致的对象，则此对象也可以被用于初始化 bytearray。
* 如果没有输入任何参数，默认就是初始化数组为0个元素。

### 2.执行系统命令（py）
```python3
    cmd = "ping %s -c 1" % serverIP     #-c(count)：发送数目；1：发送一条
    pipeConsole = os.popen(cmd)         #执行命令
    outData = pipeConsole.read()        #读取命令执行后的内容
```

### 3.Hash加密（py）
```python3
    hl = hashlib.md5()
    hl.update(userPwd.encode(encoding='utf-8'))
    userPwd = hl.hexdigest().upper()
```
>* MD5信息摘要算法（英语：MD5 Message-Digest Algorithm），一种被广泛使用的密码散列函数，可以产生出一个128位（16字节）的散列值（hash value），用于确保信息传输完整一致。
>* update：用提供的字节串更新此哈希对象(hash object)的状态
>* hexdigest：返回摘要值,以十六进制数字字符串的形式。

### 4.rfind函数（py)
```python3
str.rfind(str1, ben=0 end=len(string))
```
>返回字符串最后一次出现的位置，没有匹配返回-1
>* str1 --查找的字符串
>* ben --开始查找位置，默认0
>* end --结束查找位置，默认字符串长度

### 5.ui文件转换py文件
+ 将```Qt Designer```生成的```ui```文件转换为```.py```文件，使用如下命令:
```shell
python -m PyQt5.uic.pyuic ui    #文件路径 -o 生成的py文件的文件完整路径         这种方法生成的py文件执行的时候不会打开界面，如果想生成可直接执行后生成ui界面的py文件，可在最后加上 -x  如下
python -m PyQt5.uic.pyuic ui    #文件路径 -o 生成的py文件的文件完整路径 -x
```


## 四、QT
### 1.窗口部件大小位置(qt)
```python3
    self.ui.grpTask.setFixedHeight(grpTaskHeight - lenth*2)    #设置高度
    self.ui.lbTitle.move(self.ui.lbTitle.x(), self.ui.lbTitle.y()-lenth)    #利用自身xy坐标移动位置
```

### 2.Qtimer定时器（Qt）
```python3
    self.tmMsg = QtCore.QTimer()                   #创建定时器
    self.tmMsg.setInterval(6000)                   #设定定时时间6000毫秒，到时发出中断信号
    self.tmMsg.timeout.connect(self.onTimerMsg)    #连接槽函数onTimerMsg
    self.tmMsg.start()                             #开始定时
```
- 当定时结束时触发槽函数

### 3.WA_QuitOnClose(Qt)
```python3
    self.setAttribute(QtCore.Qt.WA_QuitOnClose, False)
```
>WA_QuitOnClose属性的主窗口关闭时，终止程序，若没有这样的主窗口，即使所有的窗口都关闭了程序也不会结束。

### 4.QLineEdit(Qt)
```python3
    self.ui.edtPassword.setEchoMode(QtWidgets.QLineEdit.Password)
```
>- QLineEdit::Normal --- 正常显示输入的字符，默认选项。
>- QLineEdit::NoEcho  ---不显示任何输入，常用于密码类型，包括密码长度
>- QLineEdit::Password  ---显示平台相关的密码掩码字符，而不是实际的字符输入。
>- QLineEdit::PasswordEchoOnEdit ---处于输入状态的时候，是正常显示字符。 输入完毕之后,使用Password形式隐藏字符  

### 5.Qt贴图（QPalette)
```python3
    bkImageFile = imgPath + 'online.png'
    self.tmBckGrd = QtGui.QPixmap(bkImageFile)
    self.resize(self.tmBckGrd.size())
    palette = QtGui.QPalette()
    palette.setBrush(QtGui.QPalette.All, QtGui.QPalette.Window, QtGui.QBrush(self.tmBckGrd))
    self.setPalette(palette)
    self.setAutoFillBackground(True)
```

### 6.移动整体窗口
```python3
	def mousePressEvent(self, a0: QtGui.QMouseEvent) -> None:
		# 鼠标左键被按下
		if a0.buttons() == QtCore.Qt.LeftButton:
			self.mousePress = True
			self.movePoint = a0.pos()

	def mouseMoveEvent(self, a0: QtGui.QMouseEvent) -> None:
		# 每次移动鼠标都会触发一次事件
		if self.mousePress:
			movePos = a0.globalPos()
			self.move(movePos - self.movePoint)

	def mouseReleaseEvent(self, a0: QtGui.QMouseEvent) -> None:
		#释放按键
		self.mousePress = False
```

### 7.贴图（不同状态，利用QSS）
```python3
	#最小化
	self.ui.minButton.setStyleSheet(("QToolButton{{border-image:url({0}{1}.png);}}"
			"QToolButton:hover{{border-image:url({0}{1}_on.png);}}"
			"QToolButton:pressed{{border-image:url({0}{1}_on.png);}}").format(imgPath, 'min'))
	self.ui.minButton.setToolTip(u'最小化')
	self.ui.minButton.clicked.connect(self.hide)

    #任务栏图标
    self.setWindowIcon(QtGui.QIcon(imgPath + 'off.png'))
```


## 五、程序结构
### 1.logon—>online
* 程序开始——》online启动——》logon启动——》onTimerLogon计时器启动——》
* 50毫秒后隐藏触发计时器——》计时器连接槽函数如下：
```python3
    def onTimerLogon(self):
    	print('start logon')     #触发计时器联动的槽函数后打印到终端
    	self.tmLogon.stop()      #关闭计时器
    	self.hide()              #隐藏online页面
    	self.logonDlg.ui.lblInfo.setText('')            #清空logon页面错误信息
    	if self.logonDlg.exec() == self.logonDlg.Rejected:        #启动logon页面，等待下一步操作，如果按确定，代表登录，继续执行if语句以外的语句，若点取消，则进入if语句，关掉接收打印信息的线程，并返回
    		self.sockTcp.close()
    		return
    	self.show()                #上述if语句跳出后则启动online页面（点确定后的情况）
    	self.trayIcon.setIcon(self.iconOn)    #系统托盘变更
    	self.getServerSetting()        #连接服务器，下载信息
    	self.updateUI()            #更新界面
```