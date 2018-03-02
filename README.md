# command.x
批量执行远程命令，结果分类统计


1.  在node.list中放入要执行的机器列表，每个机器一行

    如果机器单独有密码，在机器后用“:”分隔然后写上密码（如 10.10.10.1: 123456）

    (注意密码不要用引号引起起来)

2.  配置my.config, （不要用引号去把key或者value因起来，这个不是yaml)

3. 编写要执行的脚本 command.x ,这个脚本需要打印 RE:类型:RE，或者 RE:类型.一些信息:RE

    当前类型有Success, Fail, Ignore, Fatal。（如在shell中 ecoh RE:Success:RE  或者 echo RE:Fail.noConfigFile:RE ）

    会根据这个来进行分类, 其中Success 和Ignore 在重复执行./run的时候会被跳过。

    如果出现Fatal＊则整个任务终止

4. 运行./run 

    可以运行多次执行，Success＊ 和Ignore＊不会被重复执行，

    同时如果有Fatal的存在会直接退出，处理好Fatal删除对应文件后在执行
