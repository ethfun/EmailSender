# EmailSender
钓鱼邮件便捷发送工具（GUI）
# **程序简介**

本程序利用Python语言编写，使用Tkinter实现图形化界面，可使用Pyinstaller进行exe打包，程序主界面截图如下：
![image](https://github.com/A10ha/EmailSender/assets/60035496/77da46b8-ce46-4488-b960-8f86bdedeeda)

# **功能简介**

1. 支持腾讯企业邮、网易企业邮、阿里企业邮、自建邮服SMTP授权账号。
2. 批量发送钓鱼邮件，可暂停发送，可重置发送。
3. 伪造发件人名称与发件人邮箱。
4. 解析EML邮件原文文件，快捷利用邮件原文生成钓鱼邮件。
5. 快捷邮件正文HTML代码编辑预览，快速本地调试邮件内容。
6. 设置监听服务器，监听接收受害者是否打开邮件，适用于应急演练场景。
7. 本地日志记录，自动创建本地日志目录，记录全量日志以及错误日志。
8. 正文图片Base64编码插入，可用于插入钓鱼网页二维码等图片。

# **关键参数说明**

1. SMTP账号密码必填，由相关企业邮设置-客户端授权生成。
2. 自建SMTP优先级最高，若要使用其他官方SMTP服务器请将自建SMTP置空。
3. 监听服务器地址选填，可开启HTTP服务监听访问。
4. EML文件导入，由邮箱导出邮件，选择后，可进行邮件正文（HTML代码）编辑，通过邮件预览查看样式。
5. 收件人列表，批量发送时配置，使用txt文件指定，每个邮箱使用换行分割。

# **开发思路**

# **发送邮件函数**

利用**python**的**email**库，使用**smtplib**创建SMTP通信客户端与服务端通信发送邮件。

配置发送人信息参数实现发件人信息伪造，有些邮件管理客户端会存在代发字段。

利用在正文中添加隐藏图片代码，当受害者打开邮件时，请求攻击者监听服务器资源，达到识别邮件是否启封。

# **EML文件处理**

利用**python**的**email**库，使用**Parser()**进行邮件原文文件解析，之后针对解析出来的信息进行处理输出。

# **HTML正文编辑预览**

利用邮件原文文件解析处理的正文**HTML**信息，定向输出到**Tkinter**的**Text()**控件中，达到即时编辑。

通过**Python**的**File**类函数将**Text()**控件中的内容写入本地**temp.html**中利用**os**库执行”**start temp.html**“，利用本地浏览器打开文件，实现邮件预览。

# 本项目是仅为个人研究练习开发，禁止用于非法活动。 
# 项目开发者对软件的滥用不承担任何责任。 由使用者负责。
