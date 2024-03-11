# Chapter 1

[link_to_chapter_sub](./chapter_sub.md)

last updated: 2024.3.11

## mdbook + github pages + github actions

### 最后效果是啥样的

本地修改下 markdown， 推代码， 过不到2分钟就可以在 username.github.io/repo_name 上看到更新后的文档了

### 怎么玩

#### 先在本地玩一下 mdbook， 用 pages 发布下看看效果

##### 配环境

先搞 rust
去 https://rustup.rs/ 安装 rust

然后搞 mdbook
去 crates.io 搜索 mdbook， 最上边那个就是， 安装一下

对着 mdbook 的文档玩一下， 看看效果

##### pages

有 mdbook 之后可以先玩一下 pages

pages 是在 git repo 的 Settings 里面找 Pages， 那里有一堆部署设定， 比如从哪儿找网页的源文件， 我这里先设定为 master 分支下的 docs/ 文件夹

手动调整一下 mdbook project 的目录， 把 book/ 下面的内容复制到一个 docs/ 目录下面， 然后 push 代码

等几秒， https://superggn.github.io/pages_test/ 就有东西了

#### 优化

##### 为啥要优化， 现在不是用的挺好

感觉每次都得手动调整目录太烦了

而且渲染出来的一堆文件放在 repo 里看着很碍事

##### 啥思路
用 github actions 侦测某分支的新 commit， 一旦发现新推送， 配置 mdbook 环境在线渲染， 推送到 deployment 分支下， 让 github pages 自动部署

