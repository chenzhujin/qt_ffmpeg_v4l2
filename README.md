# QT+FFMPEG+V4L2  实时显示录制

 环境：Ubuntukylin 20.04   ,ffmpeg-4.3.1.tar.xz 库   ，Qt 5.14   

​          USB摄像头格式： YUYV 4:2:2  

功能说明：该代码实现，实时抓取摄像头数据，在QT 中显示，并循环录制10S的视频。   



# 环境配置说明： 

把ffmpeg_lib.tar.bz 包拷贝到  Ubuntu的/home/gec/目录进行解压 

 tar  -xzvf  ffmpeg_lib.tar.bz   -C   /home/gec/  



QT 中的pro 文件已经配置好相关的库路径，可以自行修改： 

```shell
QT       += core gui

greaterThan(QT_MAJOR_VERSION, 4): QT += widgets

CONFIG += c++11

# The following define makes your compiler emit warnings if you use
# any Qt feature that has been marked deprecated (the exact warnings
# depend on your compiler). Please consult the documentation of the
# deprecated API in order to know how to port your code away from it.
DEFINES += QT_DEPRECATED_WARNINGS

# You can also make your code fail to compile if it uses deprecated APIs.
# In order to do so, uncomment the following line.
# You can also select to disable deprecated APIs only up to a certain version of Qt.
#DEFINES += QT_DISABLE_DEPRECATED_BEFORE=0x060000    # disables all the APIs deprecated before Qt 6.0.0

SOURCES += \
    main.cpp \
    mainwindow.cpp
    
#头文件的路径，可以自行修改
INCLUDEPATH += /home/gec/ffmpeg/include
#库文件的路径可以自行修改
LIBS+=  -L/home/gec/ffmpeg/lib   -lavcodec   -lavdevice  -lavfilter  -lavformat -lavutil -lswresample -lswscale  -lm   -lpthread


HEADERS += \
    mainwindow.h

FORMS += \
    mainwindow.ui

# Default rules for deployment.
qnx: target.path = /tmp/$${TARGET}/bin
else: unix:!android: target.path = /opt/$${TARGET}/bin
!isEmpty(target.path): INSTALLS += target

```



环境配置完毕后利用QT 打开工程，点击运行即可。