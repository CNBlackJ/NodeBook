# Git

- `.gitignore`失效
  - 原因：之前没有添加到`.gitignore`，导致git缓存了该文件／文件夹
  - 解决方案：`git remove -r --cached .`(清除所有的缓存信息，重新建立gitignore索引，可指定文件／文件夹进行清除)

