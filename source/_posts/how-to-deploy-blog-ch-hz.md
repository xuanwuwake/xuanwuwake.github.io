---
title: 利用Hexo搭建个人博客
---

通常情况下，我们会利用Github Pages作为站点，然后利用[Hexo](https://hexo.io/zh-cn/index.html)搭建个人博客。

搭建步骤如下：

```bash
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

以上步骤运行OK后，会看到Hexo默认主题的网页，这里推荐更换主题为：Next。步骤如下：

1. 在博客站点路径下：
```bash
git clone git@github.com:next-theme/hexo-theme-next.git themes/next
```
2. 修改站点下`_config.yml`文件中的`theme`为`next`
```
theme: next
```
3. 将博客部署到Github上

修改`_config.yml`文件如下：

```bash
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repository: git@github.com:xuanwuwake/xuanwuwake.github.io.git
  branch: main
```

然后执行：

```bash
hexo deploy
```

出现问题：

1. FetchError: network timeout at: https://registry.npmjs.org/bluebird

解决方案看[这里](https://stackoverflow.com/questions/61378672/npm-err-response-timeout-while-trying-to-fetch-https-registry-npmjs-org-react)，创建~/.npmrc文件，并在这个文件中添加：

```
prefer-offline=true
```

2. hexo d命令报错 ERROR Deployer not found: git

[安装](https://blog.csdn.net/qq_21808961/article/details/84476504)git插件：
```bash
npm install hexo-deployer-git --save
```

# 自动化编译部署

```bash
# deploy.sh
hexo clean && hexo generate && hexo server && hexo deploy
```
# 资料：

- https://hexo.io/zh-cn/index.html
- http://theme-next.iissnan.com/getting-started.html
- https://www.jianshu.com/u/bdcdf3790bba
- [Hexo cannot display “next” theme](https://stackoverflow.com/questions/63405693/hexo-cannot-display-next-theme)
- https://theme-next.js.org/docs/getting-started/installation.html
- https://github.com/next-theme/hexo-theme-next/tree/master
- [hexo+github 部署个人博客](https://www.jianshu.com/p/4d359d9777a0?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)