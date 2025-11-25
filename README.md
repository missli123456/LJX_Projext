# VM Ubuntu 24.04 QT 机器视觉

## 登录ubuntu    
密码123456

## 进入MVS客户端界面
    bin（执行文件）
    doc（工业相机SDK相关文档）
    driver （Gige相机驱动安装）
    Include（SDK的头文件）
    Lib（SDK的Lib文件）
    logserver （日志服务）
    Samples（示例程序）

```
/opt/MVS/bin/MVS.sh
```
##初始进行相机画面测试（黑白）
1、在QT中打开示例文件 
```
/opt/MVS/Samples/aarch64/C++/AreaScanCamera/QtCreator/BasicDemo
```
2、进行编译
点击构建，Build All Projects,然后运行BasicDemo.pro，可能会报错：
<img width="586" height="156" alt="fb832f8b99d4ef4207727e93a0e44cb9" src="https://github.com/user-attachments/assets/c91d38d6-d46d-4eab-873a-dc0aedba68ff" />
在终端运行：
```
sudo apt update
sudo apt install libglu1-mesa-dev libgl1-mesa-dev mesa-utils
```
发现还是报错，对BasicDemo.pro进行编辑：
<img width="2392" height="1360" alt="06223d91169d7ff64120500f5bfe3b9c" src="https://github.com/user-attachments/assets/20d5432b-745b-4616-84e8-1cdab3c2966f" />
删除上图红色圈出地方，即将43行：
```
LIBS += -L$$PWD/../../../../../..//bin -L$$pwD/../../../../../../lib/64/-lMvcameracontrol
```
改成
```
LIBS += -L$$pwD/../../../../../../lib/64/-lMvcameracontrol
```
ctrl+s保存，重新构建，Build All Projects,运行BasicDemo.pro，查找设备，进行图形采集，即可。

## 代码Git上传
```
$ git add <filename>  # 将指定文件添加到暂存区中
$ git commit -m "xxx"  # 把暂存区中的文件提交到本地仓库中并添加描述信息
$ git push -u origin <branch>  # 将本地仓库的分支提交至相应的远程仓库分支
$ git clone -b <branch> <url>  # 将远程仓库的一个分支克隆到本地
$ git pull  # 从远程仓库中获取最新版本
```
