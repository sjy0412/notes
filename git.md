

##初始化
git init

##把代码存储到.git仓储中
1.把代码放到仓储门口
git add ./文件名
git add ./ 把所有的修改文件都添加到门口

2.把仓储门口的代码放到里面房间中去
git commit -m "说明"

##一次性把修改的代码放到房间
git commit --all -m "说明"


##查看当前状态
git status 可查看当前代码有没有放到仓储中去

##查看日志
git log 查看历史日志
git log --online 查看简洁版的日志


##回退到指定的版本
git reset --hard Head~0
git reset --hard 版本号 通过版本号精确回退到某一次提交时的状态

git reflog 可以看到每一次切换版本的记录

##创建分支 
git branch dev创建了一个dev分支,刚创建时与master分支里面东西一样

##提交代码到GitHub
git push 地址 master 把当前分支的内容上传到远程的master分支上

##取远程分支代码
git pull 地址 master 把远程分支的数据得到 (需要先创建一个仓储)
git clone 地址 会得到相同数据,重复次数多容易把本地数据覆盖


##ssh方式上传代码
生成公钥和私钥(两者之间是有关联的)
id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
ssh-keygen -t 用户名 -C "邮箱"
git push shh地址 master 用ssh方式上传
 

##在push和pull操作时,先pull再push

git remote add origin ssh的地址 如:git remote add origin git@github.com:sjy0412/shen-notes.git
git push -u origin master
git push
当我们在push时,加上-u参数,那么下一次push时只需要写上git push就能上传代码

##切换分支
git checkout dev 切换到指定的分支
git branch 查看当前有哪有分支

#合并分支
git merge dev 当前分支与指定分支(dev)合并
