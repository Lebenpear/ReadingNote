# Git与代码版本管理实践报告

##  实践基本信息
- 实践主题：Git与代码版本管理基础操作
- 实践时间：2026年春季学期读书实践周
- 实践目标：掌握Git基础操作、远程仓库协作流程，建立工程化开发意识

---

##  学习资料来源及相关链接
- Git 官方文档：https://git-scm.com/doc
- GitHub 官方中文教程：https://docs.github.com/zh/get-started
- 菜鸟教程 Git 基础：https://www.runoob.com/git/git-tutorial.html
- B站 Git 入门教程：https://www.bilibili.com/video/BV1FE411P7R8/
- 课程实践任务指导书：24级2026年春季学期读书实践周任务——Git与代码版本管理

---

##  实践流程（安装、配置、使用过程）

### 1. Git环境配置与本地仓库创建
1.  **安装Git**
    - 下载并安装Windows版本Git（https://git-scm.com/download/win），安装过程中保持默认选项，勾选「Git Bash Here」。
2.  **配置Git用户信息**
    打开Git Bash，执行以下命令配置全局用户信息：
    ```bash
    git config --global user.name "你的用户名"
    git config --global user.email "你的邮箱地址"
    # 验证配置
    git config --global --list
    ```
3.  **创建本地仓库**
    ```bash
    # 创建项目文件夹
    mkdir git-practice-demo
    cd git-practice-demo
    # 初始化Git仓库
    git init
    ```

### 2. 远程仓库建立与代码提交
1.  **注册Gitee账号并创建公开仓库**
    - 访问Gitee官网（https://gitee.com/）注册账号，创建公开仓库 `git-practice-demo`，复制仓库地址。
2.  **关联本地仓库与远程仓库**
    ```bash
    git remote add origin https://gitee.com/你的用户名/git-practice-demo.git
    ```
3.  **代码管理与提交**
    - 选择一份Python基础代码作为管理对象，执行多次提交与推送操作。


---

## 遇到的问题及解决方法

### 问题1：推送代码时提示权限不足（Permission denied）
- **现象**：执行 `git push` 时提示 `remote: Permission to xxx denied`，无法推送到远程仓库。-**现象：执行`git push`时提示remote: Permission to xxx denied，无法推送到远程仓库。
- **原因**：本地配置的用户名/邮箱与Gitee账号不匹配，或未配置有效的身份凭证。
- **解决方法**：
  1.  检查并修正Git配置：
      ```bash
      git config --global user.name "Gitee用户名"
      git config --global user.email "Gitee绑定邮箱"
      ```
  2.  更换为SSH方式关联远程仓库，或使用个人访问令牌（Token）作为HTTPS密码。

### 问题2：本地仓库与远程仓库历史冲突，无法合并
- **现象**：执行 `git pull` 时提示 `refusing to merge unrelated histories`，拉取失败。
- **原因**：远程仓库自动生成了README文件，与本地仓库的提交历史相互独立。
- **解决方法**：
  ```bash
  # 允许合并无关联的历史
  git pull origin master --allow-unrelated-histories
  # 处理文件冲突后重新提交并推送
  git add .
  git commit -m "合并远程仓库历史"
  git push origin master

--- 
## Git学习心得

通过本次Git与代码版本管理实践，我系统掌握了版本控制的完整流程，对Git的核心概念（工作区、暂存区、本地仓库、远程仓库）有了清晰的理解。

1. 打破了手动备份文件的低效模式：通过commit记录关键修改节点，实现了代码版本的可追溯，降低了误操作导致的代码丢失风险。

2. 体会到了规范开发的重要性：清晰的提交说明、合理的仓库结构，不仅方便自己回溯，也为后续团队协作打下了基础。

3. 提升了问题排查能力：在解决权限冲突、历史合并等问题的过程中，学会了通过报错信息定位问题、查阅官方文档解决问题的方法。

本次实践让我意识到，Git不仅是代码管理工具，更是工程化开发思维的重要载体。后续我会继续学习分支管理、冲突解决等进阶功能，将版本控制规范应用到更多课程项目中。
