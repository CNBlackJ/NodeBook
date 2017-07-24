# Git

- `.gitignore`失效
  - 原因：之前没有添加到`.gitignore`，导致git缓存了该文件／文件夹
  - 解决方案：`git rm -r --cached .`(清除所有的缓存信息，重新建立gitignore索引，可指定文件／文件夹进行清除)

- 查看git的操作日志
  - 在git操作的时候，如果对之前的操作想反悔，我们可以通过查看操作日志的方式找到需要回滚的操作记录
  - `git reflog` 查看操作日志

- release tag
	- create: `git tag <tag_name>`
	- update to remote: `git push origin <tag_name>` | `git push tags`
	- delete local tag: `git -d <tag_name>`
	- delete remote tag: `git push --delete origin <tag_name>`