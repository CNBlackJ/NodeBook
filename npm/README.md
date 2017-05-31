# Npm

早几天NPM 5.0发布了，据说是可以秒`yarn`，并且是支持生成lockfile。

The new Node.js 8 release also ships with npm 5 - the newest version of the npm CLI.

Highlights of this new npm release:

- A new, standardized lockfile feature meant for cross-package-manager compatibility (package-lock.json), and a new format and semantics for shrinkwrap,
- `–save` is no longer necessary as all installs will be saved by default,
- node-gyp now supports node-gyp.cmd on Windows,
- new publishes will now include both sha512 and sha1 checksums.

### 安装 ／ 升级

#### 安装
- 查看是否安装
	`npm -v`
- 使用`homebrew`安装
	`brew install npm`
- 使用脚本安装
	`curl http://npmjs.org/install.sh | sh`

#### 升级
- 安装最新版本（目前是5.0.0）
	`npm install npm@latest -g`

### 生成版本锁定文件（npm-shrinkwrap.json）

#### 简介
版本锁定文件的作用在于避免了同一个`package.json`下进行安装的包出现不同的版本，导致项目因为依赖版本不同而产生问题。
在5.0以前也是可以生产版本锁定文件的，这个功能在以前是比较少开发者会用到。在5.0.0中可以使用以下命令生成lockfile：

- `npm shrinkwrap`

这个命令锁定安装的依赖包的版本，因此可以精确的控制每次进行`npm install`的时候安装的版本。

#### 实际操作
- 安装当前版本的包
	`npm install`
- 确保当前安装的包可以让项目成功运行
- 生产版本锁定文件(npm-shrinkwrap.json)，该文件会记录当前包的版本信息
	`npm shrinkwrap`

### 扩展
- `npm install`是支持加环境参数（`--save` / `--save-dev` / `--production`）来安装不同包的，
	`npm shrinkwrap`也同样支持加环境参数（`--only=prod` / `--production`）来控制不同环境下的版本信息。

##### Reference
- [npmjs.com](https://docs.npmjs.com/cli/shrinkwrap)
- [cnode.org](https://cnodejs.org/topic/592e377e855efbac2cf7a4dd)