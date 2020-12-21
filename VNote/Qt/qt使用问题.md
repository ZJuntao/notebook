# 使用问题
1. 项目所在目录，使用命令：qmake -qt4， 生成Makefile文件，后使make编译
2. qt5编译：qmake udp.pro  -o Makefile ,后使用make编译
3. qt4中文会出现乱码，解决方法，在main函数中添加如下代码：
    ```cpp
    #if (QT_VERSION <= QT_VERSION_CHECK(5,0,0))
        QTextCodec::setCodecForCStrings(QTextCodec::codecForLocale());
        QTextCodec::setCodecForTr(QTextCodec::codecForName("utf8"));
    #endif
    ```
4. _T是一个宏，作用是让你的程序支持Unicode编码。
    >因为Windows使用两种字符集ANSI和UNICODE，前者就是通常使用的单字节方式，但这种方式处理像中文这样的双字节字符不方便，容易出现半个汉字的情况。而后者是双字节方式，方便处理双字节字符。