一 、设置Git的user name和email：

$ git config --global user.name "名字"

$ git config --global user.email "邮箱@邮箱.com"


二、生成新的Key：

ssh-keygen -t rsa -C "邮箱@邮箱.com"

输入密码，push需要输入密码，麻烦就不输

三、提交公钥：

1、 找到.ssh文件夹，用文本编辑器打开“id_rsa.pub”文件，复制内容到剪贴板。

2、 打开 https://github.com/settings/ssh ，点击 Add SSH Key 按钮，粘贴进去保存即可。


（一）解决每次操作都需要输入账号密码的问题

1、git config --global credential.helper store

2、在项目.git文件夹的config文件中添加

[credential]

    helper = store
    
3、在项目中pull一下，输入用户名和密码，下次再操作就不再需要输入账号密码了
