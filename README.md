# UCAS Helper
![python version](https://img.shields.io/badge/python-3.5%2B-blue)
![demo version](https://img.shields.io/badge/version-2.0.2-yellowgreen)
```angular2
*********************************************************************************
**      #   #   ###     #       ###    #  #   ###  #     ###    ###  ####      **
**      #   #  #       # #     #       #  #  #     #     #  #  #     #   #     **
**      #   #  #      #   #    ####    ####  ###   #     ###   ###   ####      **
**      #   #  #     #######      #    #  #  #     #     #     #     #  #      **
**       ###    ### ##     ##  ###     #  #   ###  ##### #      ###  #   #     **
**                            copyright@GentleCP                               **
**                            version: 2.0.2                                   **
**                github: https://github.com/GentleCP/UCASHelper               **
**                            1:course sources download                        **
**                            2:wifi login                                     **
**                            3:wifi logout                                    **
**                            4:course assess                                  **
**                            5:query grades                                   **
**                            q:exit                                           **
*********************************************************************************
```
目录
=================

   * [前言](#前言)
   * [1. 功能介绍](#1-功能介绍)
      * [1.1 课程资源下载](#11-课程资源下载)
      * [1.2 wifi登录](#12-wifi登录)
      * [1.3 课程评估](#13-课程评估)
      * [1.4 分数查询](#14-分数查询)
   * [2. 更新日志](#2-更新日志)
   * [3. 作者信息](#3-作者信息)
   * [4. 效果预览](#4-效果预览)
   * [5. 部署使用](#5-部署使用)
      * [5.1 使用前提](#51-使用前提)
      * [5.2 部署项目](#52-部署项目)
         * [5.2.1 自动部署](#521-自动部署)
         * [5.2.2 手动部署](#522-手动部署)
      * [5.3 修改配置](#53-修改配置)
      * [5.4 运行项目](#54-运行项目)
   * [6. 问题反馈](#6-问题反馈)

# 前言
原本只是一时兴起，为了方便写的UCAS课程网站小助手，帮助我自己进行课程资源快速同步。
没想到后面随着功能的增加，项目也变得小有规模起来，因此将其开放给全体UCAS同学，小助手的使用方式在下面有介绍，
十分简便（需要一点对`python`环境的了解，百度`python`的安装即可），如果你觉得本项目对你有所帮助的话，
希望你能帮我点个star，算是对作者的一点激励吧～

> 注意：由于课程网站的变动可能引发脚本失效，在失效后，我会尽量及时修复bug，并更新版本到github，
建议star项目方便接收更新消息，或者在失效时查看本项目[github链接](https://github.com/GentleCP/UCASHelper)。

# 1. 功能介绍
## 1.1 课程资源下载
国科大的课程网站在高校中已经算是很便利的了，老师可以发布ppt或其他课程资源到网站上，
学生可以登录课程网站下载需要的资源，但唯一让我感觉不爽的就是每个资源（如ppt），
只能一个个单独下载，没有批量下载的选项。另一方面，每次网站发布了新的资源，
我都要登录课程网站一个个点，真的心累。要是有个脚本可以直接将我本地的课程资源，
与课程网站一键同步就好了。所以就写了一个可用自动同步所有课程资源到本地的项目。

> 现在可以按照学期同步自己需要的资源，而不用将之前学期的一并同步

## 1.2 wifi登录
提供了自动登录的功能，且允许添加多个账号，当一个账号流量使用完后，可用下一个账号自动登录，
每月自动更新。出于隐私保护，项目不直接提供爆破的账号密码信息（以防被外来人员利用），在校学生可参考**5.部署使用**，
破解新的账号。
> 爆破需在校园网环境下，请确保你已正确连接校园网（建议有线）且未登录校园网。
爆破时间较长（慢的时候2-3个小时），因此建议晚上睡觉的时候开启，
早上的时候一般已经爆破完成1-2个账号。

- 校园网对单个设备登录有限制，因此多进程的速度与单进程差别不大
- 一个账号流量有25GB，因此一般破解1-2个账号加上自己的就够个人使用了
- 对于破解的账号，请**不要修改密码**，方便自己也方便他人:)
- 当然你也可以直接找要好的师兄师姐，借用他们的账号添加到accounts.json中，
省时省力QAQ
- 破解的账号都是往年的已经离开雁栖湖回所的师兄师姐的！
**请不要利用本项目对还在雁栖湖上课的同学的账号进行破解！！！**

## 1.3 课程评估 
新增了课程评估的功能，在主界面中选择4即可进行课程评估，评估的等级默认选择5，
因为会用脚本评估的大多是怕麻烦的人，如果有个别老师或课程让你觉得十分不靠谱，
根本无益，建议还是手动去修改下对应的评估，虽然不知道是否真的对教改有用，
起码得让那课程老师心里有点数呀~
> 评估之前请进入`settings.py`修改一下主观评估的内容，别都和我评估一样了喂~

![](img/5-2.png)


## 1.4 分数查询
分数查询功能重新上线！现在可以在程序主页选择功能5(query grades)来查询自己的所有成绩，
显示效果如下：

![](img/1.7.0.png)

# 2. 更新日志
- [2.0.2] 修复了因课程网站选课系统添加头部检查导致的**课程评估，分数查询**功能的失效。
- [2.0.1] 对整体代码进行了重构，解决因课程网站`http`,`https`协议切换导致的访问出错问题，
同时更改了项目接口，方便小白和专业人士操作。以前均通过可视化`UI`界面进行操作，现在用户可选择`UI`和命令行两种模式，具体见**5.部署使用**。
对各个功能测试结果如下：
    - [x] 课程资源同步
    - [x] 分数查询
    - [ ] 自动评教：由于课程网站评教操作关闭，尚未测试
    - [ ] 校园网登录：由于不在学校，尚未测试
    - [ ] 校园网账号破解：同上
    > 未测试内容基本上沿用了之前的代码，按照常理不会出错，如果有问题，欢迎提出`issue`
  
- [1.7.2] 修复了因课程主站使用http协议导致的错误  
    > GKD的课程主站偶尔抽风，一会用https，一会用http，导致访问端口出现问题，现统一将用到的url放到`settings.py/URLS`中，
    当主站修改应用协议时修改对应url的协议即可。例如`'base_url':'http://jwxk.ucas.ac.cn'`>`'base_url':'https://jwxk.ucas.ac.cn'`,
    目前没时间完美适配这个问题（对代码重构较多）。
- [1.7.1] 修改了主页的部分显示内容，添加版本信息，去除网站链接
- [1.7.0] 添加了分数查询功能并修复了课程评估失败的问题
- [1.6.0]  
    > 文件同步添加了进度条，方便查看文件同步信息，但请注意，若下载过程中未完成中断任务需将下载一半的文件删除，否则不会更新
    ![](img/1.6.0.png)
- [1.5.1]  
    
    > 修复下载全部课程资源时没有打开文件目录的选项问题，当无更新的时候自动退出应用
    
- [1.5.0]  
    - 课程资源同步后有新的资源时会提示是否开启资源所在目录，简便查看文件操作，如下
        ![](img/1.5.0-1.png)
    - 允许添加不希望被同步的课程内容：在同步所有的时候有一门课的资源并没什么卵用，但为了一门而去一个个同步其他的又略显麻烦，
    因此添加了一个`FILTER_LIST`，存放不想被同步的课程目录。打开`settings.py`，找到`FILTER_LIST`，
    将不想被同步的课程全名（如`没啥用课19-20春季`），添加到列表当中，如下：
        ![](img/1.5.0-2.png)
    
    - 新版本在同步更新完成后会自动退出，不需要再手动退出程序
    
- [1.4.3]
    > 修复了当同时存在多个文件夹和文件时不会下载与文件夹同目录的文件的问题，如下图所示：
    ![](img/fix_1.4.3-1.png)
    
- [1.4.2]  
    
    > 解决了当课程网站存在文件夹时无法获取到课程资源同步的问题，一开始并未考虑到老师创建文件夹
    
- [1.4.1]  
    
    > 在课程资源选项中可以选择仅同步某个学期(春季，夏季，秋季)课程

# 3. 作者信息
- name: 董超鹏
- nickname: GentleCP
- e-mail: 574881148@qq.com
- website: https://www.gentlecp.com

# 4. 效果预览
- 小白使用窗口  
    ![](img/2-1.png)
- 自动登录校园网  
    ![](img/3-1.png)
- 校园网账号破解  

- 自动查分  
    ![](img/4-1.png)
- 显示本学期课程列表  
    ![](img/1-1.png)
    
- 同步所有课程资源到本地  
    ![](img/1-2.png)
- 同步指定课程的资源到本地      
    ![](img/1-3.png)
- 同步指定课程的指定一个资源到本地  
  
- 自动评估课程和教师  
    ![](img/5-1.png)

# 5. 部署使用

## 5.1 使用前提
项目采用python语言编写，需要你本地装有python3环境（建议python3.5+），如果采用`git`方式克隆，需先安装好`git`


## 5.2 部署项目
提供两种部署使用方法：`自动化部署`(懒人推荐)和`手动部署`，前者在`windows`环境下要求安装`git`，采用`git`提供的终端（需要用到`shell`命令，`windows`cmd不支持）

### 5.2.1 自动部署
> 注意：如果选择采用虚拟环境，请确保`mkvirtualenv`命令可用。
- 采用虚拟环境（推荐） 
    - `pip`:多为`windows`用户,进入`git`提供的`bash`终端
        ```text
        wget https://github.com/GentleCP/UCASHelper/archive/master.zip && unzip master.zip && cd UCASHelper-master;mkvirtualenv ucashelper && pip install -r requirements.txt         
        ```
    - `pip3`:`mac`,`linux`用户
        ```text
        wget https://github.com/GentleCP/UCASHelper/archive/master.zip && unzip master.zip && cd UCASHelper-master;mkvirtualenv ucashelper && pip3 install -r requirements.txt
        ```
- 不采用虚拟环境 
    - `pip`
        ```text
        wget https://github.com/GentleCP/UCASHelper/archive/master.zip && unzip master.zip && cd UCASHelper-master && pip install -r requirements.txt         
        ```
    - `pip3`
        ```text
        wget https://github.com/GentleCP/UCASHelper/archive/master.zip && unzip master.zip && cd UCASHelper-master && pip3 install -r requirements.txt
        ```
### 5.2.2 手动部署
1. 克隆本项目到本地（需要`git`）或下载源代码压缩包或下载`realease`版本代码(推荐)  
    ```text
    git clone https://github.com/GentleCP/UCASHelper.git
    ```
    
2. 进入项目目录安装依赖包
    ```text
    pip install -r requirements.txt  # 强烈建议使用虚拟环境
    conda env create -f environment.yml  # 如果采用conda环境
    ```


## 5.3 修改配置
根据需求修改配置文件:`settings.py`,`accounts.json`
- 获取课程资源
    - 进入[settings.py](settings.py)，找到`USER_INFO`修改你自己的用户名和密码
    - 修改`SOURCE_DIR`，这个目录是所有课程资源存放的目录，根据你的个人需求修改  
        
        > 例如`D:/UCAS-sources`
    > 在校园网内无需登录wifi，直接可登录课程网站
- 登录wifi  
    - wifi登录需修改根目录下的`accounts.json`，添加到useful_accounts中，格式如下：
        ```text
          {
              "useful_accounts": [
                {
                   "stuid":"xxx",
                   "pwd":"xxx"
                },
                {
                    "stuid":"xxx",
                    "pwd":"xxx"
                }
               
              ],
              "useless_accounts": [],
              "current_month": 12
            }
        ```
        每个账号一个，允许存储多个账号，当遇到一个账号流量不够的时候自动切换到下一个账号登录



## 5.4 运行项目

当确认配置信息修改完毕后，可以在终端或cmd下通过执行`python ucashelper.py ui`来启动小白操作窗口，同时也可以根据需要直接在命令行传入不同参数执行相应的操作，具体如下：

```python
python ucashelper.py --help # 查看命令使用帮助，直接运行python ucashelper.py 效果等同
python ucashelper.py ui # 小白操作窗口

python ucashelper.py down # 下载课程资源
python ucashelper.py grade # 查看成绩
python ucashelper.py hack # 破解wifi账号
python ucashelper.py login # 登录校园网，确保在校园网环境下未登录情况执行
python ucashelper.py logout # 登出校园网
python ucashelper.py assess # 自动评教，评教内容在settings.py中设置
```




# 6. 问题反馈
对项目如有任何问题或修改意见，欢迎提交`issue`或者邮件私信给我～