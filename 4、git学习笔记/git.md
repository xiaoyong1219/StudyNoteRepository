#### 一、git命令行提交 代码

1. **先切换分支** 

   ```shell
   git checkout develop
   ```

2. **add 以及commit到本地仓库**

   ```shell
   git add pom.xml
   ```

   ```shell
   git commit pom.xml -m '提交pom.xml文件'
   ```

3. **先更新远程仓库代码到本地仓库**

   ```shell
   git pull origin develop
   ```

4. **提交代码到远程仓库**

   ```shell
   git push -u origin develop
   ```



#### 二、git命令行删除远程仓库文件

1. **先切换分支**

   ```shell
   git checkout develop
   ```

2. **删除文件或者文件夹**

   ```shell
   git rm -r --cached pom.xml
   ```

3. **提交，添加操作说明**

   ```shell
   git commit -m '删除pom.xml文件'
   ```

4. **将本次更改更新到远程仓库**

   ```shell
   git push -u origin develop
   ```

   