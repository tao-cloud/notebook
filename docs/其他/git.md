# git操作

## git关联本地项目到远程仓库

- 初始化一个本地git仓库

  ```she
  git init
  ```

- 添加当前目录下的文件到本地仓库

  ~~~shell
  git add .
  ~~~

- 提交文件到仓库

  ~~~shell
  git commit -m "注释"
  ~~~

- 关联远程仓库

  ~~~shell
  $ git remote add origin https://github.com/tao-cloud/tt.git
  ~~~

- 推送本地项目到仓库

  ~~~shell
  git push -u origin master
  ~~~

  

