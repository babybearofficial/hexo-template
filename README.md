# hexo-template

初次接触 `Hexo` 和 `Github Actions`, 折腾了半天才搞定，为了更快的将 `Hexo` 静态站点部署到 `Github Pages`, 就创建了此仓库，`Fork` 此仓库后修改一些参数就可以直接写作了.

所有 `Hexo` 配置均采用默认, 只更改了主题为 [cactus](https://github.com/probberechts/hexo-theme-cactus).

## 使用方式

### `Fork`

先 `Fork` 此仓库

### 生成 `SSH` 密钥

```
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f gh-pages -N ""
```

使用以上命令会生成 `gh-pages` 和 `gh-pages.pub` 两个文件, 一个是 `私钥`, 一个是 `公钥`. 按照以下步骤设置密钥：

1. 打开仓库设置 `Settings`
2. 点击 `Deploy Keys` 选项, 将 `gh-pages.pub` 文件中的内容粘贴进去, 名字随便起
3. 点击 `Secrets` 选项, 将 `gh-pages` 文件中的内容粘贴进去, 名称设置为 `ACTIONS_DEPLOY_KEY`, 因为这里设置的名称需要在 `Github Actions` 配置中使用, 所以要对应.

### 开启 `Github Actions`

`Fork` 的仓库默认不开启 `Actions`, 在仓库页面手动点击 `Actions` 选项, 根据提示开启即可

### 访问博客

博客默认部署在 `gh-pages` 分支, 稍等几分钟后, 尝试访问 `https://<你的 GitHub 用户名>.github.io/<repository 的名字>` 即可判断是否部署成功.

### 克隆到本地

将博客克隆到本地, 编写博客只需将 `markdown` 文件 `push` 到仓库, 就会触发 `Github Actions` 生成 `静态页面` 部署到 `gh-pages` 分支.
