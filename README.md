# Hexo配置搭建
## Hexo安装
* git环境
* node.js环境

## Hexo版本
``` shell
Administrator@WAY-PC MINGW64 /e/hexo (hexo)
$ hexo version
hexo: 3.2.2
hexo-cli: 1.0.2
os: Windows_NT 6.1.7601 win32 x64
http_parser: 2.5.2
node: 4.4.4
v8: 4.5.103.35
uv: 1.8.0
zlib: 1.2.8
ares: 1.10.1-DEV
icu: 56.1
modules: 46
openssl: 1.0.2h
```

## 利用git解决hexo博客多PC间同步问题
新建git仓库时，创建分支hexo，将分支hexo作为默认仓库，hexo文件夹映射到该仓库
/hexo/.gitignore 配置屏蔽发布生成文件
```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
.deploy_git/
```

```shell
Administrator@WAY-PC MINGW64 /e/hexo (hexo)
$ git remote show hexo
* remote hexo
  Fetch URL: https://github.com/codevolutionway/codevolutionway.github.io.git
  Push  URL: https://github.com/codevolutionway/codevolutionway.github.io.git
  HEAD branch: hexo
  Remote branches:
    hexo   tracked
    master tracked
  Local branch configured for 'git pull':
    hexo merges with remote hexo
  Local ref configured for 'git push':
    hexo pushes to hexo (up to date)

```

/hexo/_config.yml 配置发布为git仓库master分支
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/codevolutionway/codevolutionway.github.io.git
  branch: master
```

* 综上
实现了 `hexo g` 直接发布,`git commit` 直接提交
多PC间，首次使用hexo init后git pull拉取更新，后续正常使用即可。
