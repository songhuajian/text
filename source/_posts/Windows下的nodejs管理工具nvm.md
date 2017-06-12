---
title: Windows下的nodejs管理工具nvm
date: 2016-10-15 17:01:16
tags:
---
	1. github上下载nvm管理工具
		https://github.com/coreybutler/nvm-windows.git
		最好在nvm外加一层目录
---
	2. 生成配置文件和环境变量
		用管理员身份打开install.cmd
		输入nvm路径
		可能需要两次
		编辑生成的settings.txt
		root: D:\develop\nvm (不用改)
		path: D:\develop\nodejs (改成nvm同级即可)
---
	3. 修改生成的环境变量
		path: D:\develop\nodejs
		NVM_SYMLINK:D:\develop\nodejs
		NPM_HOME:D:\develop\nvm\npm
		path:%NPM_HOME%
---
	4. 设置使用版本
		nvm list
		nvm use *.*.*
		nvm list或者node -v
---
	5. 设置node下载和缓存
		用户文件夹下建立.npmrc
		设置
		cache=D:\develop\nvm\npm-cache
		prefix=D:\develop\nvm\npm
---
	6. 使用npm install -g ***测试是否完成