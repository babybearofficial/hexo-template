# hexo-template

初次接触 `Hexo` 和 `Github Actions`, 折腾了半天才搞定，为了更快的将 `Hexo` 静态站点部署到 `Github Pages`, 就创建了此仓库，`Fork` 此仓库后修改一些参数就可以直接写作了.

所有 `Hexo` 配置均采用默认, 只更改了主题为 [cactus](https://github.com/probberechts/hexo-theme-cactus).

## 预览

[https://abyssknight.github.io/hexo-template/](https://abyssknight.github.io/hexo-template/)

## 使用方式

### `Fork`

先 `Fork` 此仓库

### 开启 `Github Pages`

`Fork` 后 `Pages` 默认就开启了, 但是并不起作用, 原因未知, 所以需要手动再开启一次, 点击仓库 `Settings` 然后下拉找到 `Github Pages`, 将 `gh-pages` 分支改成 `master` 分支, 然后再切换回来, 稍等几分钟即可访问.

### 生成 `SSH` 密钥

```
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f gh-pages -N ""
```

使用以上命令会生成 `gh-pages` 和 `gh-pages.pub` 两个文件, 一个是 `私钥`, 一个是 `公钥`. 按照以下步骤设置密钥：

1. 打开仓库设置 `Settings`
2. 点击 `Deploy Keys` 选项, 添加新的 `Key`, 将 `gh-pages.pub` 文件中的内容粘贴进去, 名字随便起, 选中 `Allow write access` 允许写权限.
3. 点击 `Secrets` 选项, 将 `gh-pages` 文件中的内容粘贴进去, 名称设置为 `ACTIONS_DEPLOY_KEY`, 因为这里设置的名称需要在 `Github Actions` 配置中使用, 所以要对应.

### 开启 `Github Actions`

`Fork` 的仓库默认不开启 `Actions`, 在仓库页面手动点击 `Actions` 选项, 根据提示开启即可.

### 修改配置

由于采用了博客路径在 `*/<仓库名>` 下, 所以生成静态资源文件请求路径也要在 `<仓库名>` 下, 所以修改 `Hexo` 配置文件 `_config.yml` 找到 `root` 属性, 改成自己的仓库名即可.

### 克隆到本地

将博客克隆到本地, 编写博客只需将 `markdown` 文件 `push` 到仓库, 就会触发 `Github Actions` 生成 `静态页面` 部署到 `gh-pages` 分支.
