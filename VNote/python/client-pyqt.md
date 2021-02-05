# client-pyqt
## 1.Socket
```python
    socket.gethostname                                      #返回当前主机名
    s=socket.socket(socket.AF_INET, socket.SOCK_DGRAM)      #创建套接字
    s.getsocketname()[0]                                    #获取当前主机ip
```

## 2.知识点整理
### rfind函数（py)
``str.rfind(str1, ben=0 end=len(string))``
>返回字符串最后一次出现的位置，没有匹配返回-1
>* str1 --查找的字符串
>* ben --开始查找位置，默认0
>* end --结束查找位置，默认字符串长度

### Qtimer定时器（Qt）
```python
self.tmMsg = QtCore.QTimer()                   #创建定时器
self.tmMsg.setInterval(6000)                   #设定定时时间6000毫秒，到时发出中断信号
self.tmMsg.timeout.connect(self.onTimerMsg)    #连接槽函数onTimerMsg
self.tmMsg.start()                             #开始定时
```
- 当定时结束时触发槽函数

### WA_QuitOnClose(Qt)
```python
self.setAttribute(QtCore.Qt.WA_QuitOnClose, False)
```
>WA_QuitOnClose属性的主窗口关闭时，终止程序，若没有这样的主窗口，即使所有的窗口都关闭了程序也不会结束。

### QLineEdit(Qt)
```python
self.ui.edtPassword.setEchoMode(QtWidgets.QLineEdit.Password)
```
>- QLineEdit::Normal --- 正常显示输入的字符，默认选项。
>- QLineEdit::NoEcho  ---不显示任何输入，常用于密码类型，包括密码长度
>- QLineEdit::Password  ---显示平台相关的密码掩码字符，而不是实际的字符输入。
>- QLineEdit::PasswordEchoOnEdit ---处于输入状态的时候，是正常显示字符。 输入完毕之后,使用Password形式隐藏字符  

### Hash加密（py）
```python
hl = hashlib.md5()
hl.update(userPwd.encode(encoding='utf-8'))
userPwd = hl.hexdigest().upper()
```
>* MD5信息摘要算法（英语：MD5 Message-Digest Algorithm），一种被广泛使用的密码散列函数，可以产生出一个128位（16字节）的散列值（hash value），用于确保信息传输完整一致。
>* update：用提供的字节串更新此哈希对象(hash object)的状态
>* hexdigest：返回摘要值,以十六进制数字字符串的形式。

### 执行系统命令（py）
```python
cmd = "ping %s -c 1" % serverIP     #-c(count)：发送数目；1：发送一条
pipeConsole = os.popen(cmd)         #执行命令
outData = pipeConsole.read()        #读取命令执行后的内容
```

### json库
```python
userParam = json.loads(retJson)
```
>- retJson：json字符串
>- json.dumps()函数是将一个Python数据类型列表进行json格式的编码（可以这么理解，json.dumps()函数是将字典转化为字符串）
>- json.loads()函数是将json格式数据转换为字典（可以这么理解，json.loads()函数是将字符串转化为字典）