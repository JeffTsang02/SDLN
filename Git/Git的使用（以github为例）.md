---
share: "true"
---

### 1 什么是 Git？

**Git** 是一个分布式版本控制系统，用于跟踪文件的更改，特别是代码文件。它允许多个开发者协作开发，记录项目的历史变更，回溯到以前的版本，并管理不同的开发分支。

**主要特点**：

- **分布式**：每个开发者都有完整的代码库副本。
- **高效**：处理大规模项目时表现出色。
- **灵活**：支持各种非线性开发流程（如分支、合并）。
- **安全**：通过 SHA-1 哈希算法确保代码完整性。

### 2 Git 的安装与配置

#### 2.1 安装 Git

**Windows**：

1. 访问 [Git 官方下载页面](https://git-scm.com/download/win)。
2. 下载适用于 Windows 的安装程序。
3. 运行安装程序，按照提示完成安装。建议保持默认选项，特别是 PATH 配置。

**macOS**：

1. 使用 [Homebrew](https://brew.sh/) 安装（如果未安装 Homebrew，请先安装）。
   
   ```bash
   brew install git
   ```
   
2. 或者，访问 [Git 官方下载页面](https://git-scm.com/download/mac) 下载并安装。

**Linux**：

- **Debian/Ubuntu**：

  ```bash
  sudo apt update
  sudo apt install git
  ```

- **Fedora**：

  ```bash
  sudo dnf install git
  ```

- **Arch Linux**：

  ```bash
  sudo pacman -S git
  ```

#### 2.2 配置 Git

安装完成后，需要进行基本配置，设置用户名和邮箱，这些信息将出现在你的提交记录中。

打开终端（命令行）并执行以下命令：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

**示例**：

```bash
git config --global user.name "张三"
git config --global user.email "zhangsan@example.com"
```

你可以通过以下命令查看配置是否成功：

```bash
git config --list
```

**输出示例**：

```
user.name=张三
user.email=zhangsan@example.com
...
```

### 3 Git 的基本概念

在深入使用 Git 之前，了解一些基本概念是非常重要的。

#### 3.1 仓库（Repository）

**仓库**是项目的代码库，包含了所有的文件及其历史记录。Git 仓库分为两种：

- **本地仓库**：存储在你电脑上的仓库。
- **远程仓库**：存储在服务器上的仓库，如 GitHub、GitLab 或 Bitbucket。

#### 3.2 工作区（Working Directory）

**工作区**是你当前正在工作的文件夹，包含项目的最新版本。

#### 3.3 暂存区（Staging Area）

**暂存区**是一个临时区域，用于存放将要提交的更改。

#### 3.4 提交（Commit）

**提交**是对项目的一个快照，记录了当前项目的状态。

#### 3.5 分支（Branch）

**分支**是项目开发的独立线索，可以并行开发不同的功能，互不干扰。

### 4 Git 的基本命令

以下是一些常用的 Git 命令，帮助你进行基本的版本控制操作。

#### 4.1 初始化仓库

在项目目录中初始化一个新的 Git 仓库。

```bash
git init
```

**示例**：

```bash
mkdir my-project
cd my-project
git init
```

#### 4.2 克隆仓库

从远程仓库克隆一个现有的仓库到本地。

```bash
git clone <仓库地址>
```

**示例**：

```bash
git clone https://github.com/username/repository.git
```

#### 4.3 查看仓库状态

查看当前仓库的状态，了解哪些文件被修改、哪些文件在暂存区等。

```bash
git status
```

#### 4.4 添加文件到暂存区

将文件的更改添加到暂存区，为提交做准备。

```bash
git add <文件名>
```

**添加单个文件**：

```bash
git add index.html
```

**添加所有更改的文件**：

```bash
git add .
```

#### 4.5 提交更改

将暂存区的更改提交到仓库。

```bash
git commit -m "提交说明"
```

**示例**：

```bash
git commit -m "添加了待办事项功能"
```

#### 4.6 查看提交历史

查看项目的提交历史，了解每次提交的详情。

```bash
git log
```

**常用选项**：

- `git log --oneline`：以简洁的一行形式显示提交历史。
- `git log --graph --decorate --all`：以图形化方式显示分支和合并情况。

#### 4.7 创建和切换分支

**创建新分支**：

```bash
git branch <分支名>
```

**示例**：

```bash
git branch feature/add-login
```

**切换到指定分支**：

```bash
git checkout <分支名>
```

**示例**：

```bash
git checkout feature/add-login
```

**简化创建并切换分支**（Git 2.23+）：

```bash
git switch -c <分支名>
```

**示例**：

```bash
git switch -c feature/add-login
```

#### 4.8 合并分支

将一个分支的更改合并到当前分支。

```bash
git merge <分支名>
```

**示例**：

```bash
git checkout main
git merge feature/add-login
```

#### 4.9 删除分支

删除不再需要的分支。

```bash
git branch -d <分支名>
```

**示例**：

```bash
git branch -d feature/add-login
```

#### 4.10 推送更改到远程仓库

将本地仓库的更改推送到远程仓库。

```bash
git push origin <分支名>
```

**示例**：

```bash
git push origin main
```

#### 4.11 拉取远程仓库的更改

从远程仓库获取最新的更改并合并到本地仓库。

```bash
git pull
```

### 5 使用 GitHub 进行协作

**GitHub** 是一个基于 Git 的远程仓库托管服务，广泛用于开源项目和团队协作。以下是如何使用 GitHub 与 Git 结合进行项目管理。

#### 5.1 创建 GitHub 账号

1. 访问 [GitHub 官网](https://github.com/)。
2. 点击右上角的“Sign up”按钮，按照提示完成注册。

#### 5.2 创建一个新的仓库

1. 登录 GitHub 后，点击右上角的“+”号，选择“New repository”。
2. 输入仓库名称（如 `my-vue-app`）。
3. 选择公开（Public）或私有（Private）。
4. 可选择初始化仓库（Initialize this repository with a README）。
5. 点击“Create repository”。

#### 5.3 将本地仓库连接到 GitHub

在本地项目目录中，添加远程仓库地址并推送代码。

**步骤**：

1. **添加远程仓库**：

   ```bash
   git remote add origin https://github.com/你的用户名/仓库名.git
   ```

   **示例**：

   ```bash
   git remote add origin https://github.com/zhangsan/my-vue-app.git
   ```

2. **推送代码到远程仓库**：

   ```bash
   git push -u origin main
   ```

   > **注意**：如果你的默认分支不是 `main`，请将 `main` 替换为相应的分支名。

#### 5.4 分支管理与 Pull Request

**分支管理**：

在团队协作中，通常使用分支来开发新功能，避免直接在 `main` 分支上进行开发，减少冲突。

**Pull Request（PR）**：

完成某个功能开发后，通过 Pull Request 将分支的更改合并到主分支。这有助于代码审查和质量控制。

**步骤**：

1. **在 GitHub 上创建 Pull Request**：

   - 访问你的仓库页面。
   - 切换到你要合并的分支。
   - 点击“Compare & pull request”按钮。
   - 填写 Pull Request 的标题和描述。
   - 点击“Create pull request”。

2. **审查并合并 Pull Request**：

   - 其他团队成员可以查看、评论和审查代码。
   - 确认无误后，点击“Merge pull request”按钮，将更改合并到主分支。

### 6 Git 的高级用法

在掌握了 Git 的基本命令后，以下是一些更高级的用法，帮助你更高效地管理代码。

#### 6.1 查看提交差异

查看不同提交之间的差异，了解具体更改内容。

```bash
git diff <提交1> <提交2>
```

**示例**：

```bash
git diff abc123 def456
```

#### 6.2 回退到以前的版本

将仓库回退到某个历史提交。

```bash
git checkout <提交哈希>
```

**示例**：

```bash
git checkout abc123
```

> **注意**：这种方式会进入“分离头指针”状态，建议使用 `git revert` 或 `git reset` 进行回退操作。

---

要回退本地 Git 仓库的版本，可以根据您当前的需求选择不同的方法。以下是几种常见的回退场景及其对应的操作步骤：

##### 场景 1：撤销未提交的更改

###### 1. 撤销工作目录中对文件的修改（未暂存）

如果您修改了某些文件，但尚未将其添加到暂存区（即未执行 `git add`），可以使用以下命令撤销这些更改：

```bash
git checkout -- <文件名>
```

**示例**：

```bash
git checkout -- src/main/java/com/example/MyClass.java
```

**注意**：此操作会丢弃工作目录中的未保存更改，无法恢复，请谨慎使用。

###### 2. 撤销所有工作目录中的未暂存更改

如果您希望一次性撤销所有未暂存的更改，可以使用：

```bash
git checkout -- .
```

或

```bash
git restore --source=HEAD --staged --worktree .
```

###### 3. 撤销已暂存但未提交的更改

如果您已经使用 `git add` 将更改添加到暂存区，但尚未提交，可以使用以下命令将更改从暂存区移除，同时保留工作目录中的修改：

```bash
git reset HEAD <文件名>
```

**示例**：

```bash
git reset HEAD src/main/java/com/example/MyClass.java
```

要一次性撤销所有已暂存的更改：

```bash
git reset HEAD .
```

##### 场景 2：回退到之前的提交

###### 1. 使用 `git reset` 回退提交

`git reset` 可以将当前分支的指针移动到指定的提交，并根据参数的不同选择保留或丢弃工作目录中的更改。

a. 回退到指定提交，并保留工作目录中的更改（软回退）

```bash
git reset --soft <提交哈希>
```

**作用**：移动分支指针到指定提交，保留所有更改在暂存区。适用于需要重新提交的情况。

b. 回退到指定提交，并将更改移出暂存区（混合回退，默认选项）

```bash
git reset --mixed <提交哈希>
```

或简写为：

```bash
git reset <提交哈希>
```

**作用**：移动分支指针到指定提交，保留工作目录中的更改，但将更改从暂存区移除。

c. 回退到指定提交，并丢弃工作目录中的更改（硬回退）

```bash
git reset --hard <提交哈希>
```

**作用**：将分支指针移动到指定提交，丢弃所有之后的提交和工作目录中的更改。**此操作不可逆，请谨慎使用**。

**示例**：

```bash
git reset --hard e2ebc594
```

###### 2. 查找目标提交的哈希值

您可以使用 `git log` 查看提交历史，并找到您想要回退到的提交哈希值：

```bash
git log --oneline
```

输出示例：

```
e2ebc59 feat: 完成资产识别系统的主要功能
a1b2c3d fix: 修复资产识别系统中的空指针异常
...
```

在上述示例中，`e2ebc59` 是一个提交哈希值。

##### 场景 3：使用 `git revert` 撤销某次提交

与 `git reset` 不同，`git revert` 不会修改提交历史，而是创建一个新的提交来撤销指定的提交。这在已经将提交推送到远程仓库后尤为有用，因为它不会影响其他协作开发者的历史。

###### 1. 撤销指定的提交

```bash
git revert <提交哈希>
```

**示例**：

```bash
git revert e2ebc594
```

**作用**：生成一个新的提交，内容是撤销 `e2ebc594` 这个提交的更改。

###### 2. 撤销多个提交

如果需要撤销多个连续的提交，可以使用 `git revert` 的范围选项：

```bash
git revert <起始提交哈希>..<结束提交哈希>
```

**示例**：

```bash
git revert a1b2c3d..e2ebc594
```

**注意**：`git revert` 会逐个生成撤销提交，适合在共享分支上使用。

##### 场景 4：回退到远程分支的状态

如果您希望将本地分支回退到与远程分支（如 `origin/feature-zcsb`）一致，可以使用以下命令：

```bash
git fetch origin
git reset --hard origin/feature-zcsb
```

**作用**：首先从远程仓库获取最新的更改，然后将本地 `feature-zcsb` 分支重置为远程分支的状态，丢弃本地所有未推送的更改。

**注意**：此操作会丢弃本地未保存的更改，无法恢复，请谨慎使用。

##### 常见问题与注意事项

1. **误操作导致数据丢失怎么办？**

   - 如果您误用了 `git reset --hard` 并丢失了重要更改，可以尝试使用 `git reflog` 查找丢失的提交哈希，然后使用 `git reset` 恢复。

   ```bash
   git reflog
   git reset --hard <丢失提交的哈希>
   ```

2. **在回退前保留当前状态**

   - 如果不确定是否需要回退，可以创建一个新的分支保存当前状态，以防需要恢复：

   ```bash
   git branch backup-branch
   ```

3. **回退后如何推送更改到远程仓库**

   - 如果使用 `git reset` 回退了提交，并且需要强制推送到远程仓库（**注意**：这可能会覆盖远程仓库的历史，影响其他协作开发者，需谨慎操作）：

   ```bash
   git push origin feature-zcsb --force
   ```

   - 建议在强制推送前与团队成员沟通，确保不会影响他人的工作。

##### 总结

回退本地 Git 仓库的版本有多种方法，具体选择取决于您的需求和当前的开发状态。以下是关键步骤的简要总结：

1. **撤销未提交的更改**：
   - 撤销工作目录中的修改：`git checkout -- <文件名>`
   - 撤销所有未暂存的更改：`git checkout -- .` 或 `git restore --source=HEAD --staged --worktree .`

2. **回退到之前的提交**：
   - 软回退：`git reset --soft <提交哈希>`
   - 混合回退：`git reset --mixed <提交哈希>` 或 `git reset <提交哈希>`
   - 硬回退：`git reset --hard <提交哈希>`

3. **使用 `git revert` 撤销特定提交**：
   - `git revert <提交哈希>`

4. **回退到远程分支的状态**：
   - `git fetch origin`
   - `git reset --hard origin/<分支名>`


---


#### 6.3 解决合并冲突

在合并分支时，可能会出现冲突。以下是解决冲突的基本步骤：

1. **识别冲突文件**：

   Git 会标记出有冲突的文件。

2. **手动编辑冲突文件**：

   打开冲突文件，找到冲突标记（`<<<<<<`, `======`, `>>>>>>`），手动选择或合并代码。

3. **添加已解决的文件到暂存区**：

   ```bash
   git add <文件名>
   ```

4. **完成合并提交**：

   ```bash
   git commit
   ```

#### 6.4 标签（Tags）

标签用于标记特定的提交，通常用于发布版本。

**创建标签**：

```bash
git tag -a v1.0 -m "版本 1.0"
```

**推送标签到远程仓库**：

```bash
git push origin v1.0
```

**查看所有标签**：

```bash
git tag
```

### 7 Git 的最佳实践

- **频繁提交**：保持每次提交的更改量适中，便于追踪和回溯。
- **有意义的提交信息**：清晰描述每次提交的目的和内容。
- **使用分支开发**：为每个新功能或修复创建独立的分支，避免影响主分支。
- **定期推送代码**：将本地更改及时推送到远程仓库，避免数据丢失。
- **代码审查**：通过 Pull Request 进行代码审查，确保代码质量。

---

## 练习与互动

### 练习 1：初始化一个新的 Git 仓库

请按照以下步骤操作：

1. **创建项目目录**：

   如果你已经有一个项目，可以跳过此步。否则，创建一个新的项目目录。

   ```bash
   mkdir my-git-project
   cd my-git-project
   ```

2. **初始化 Git 仓库**：

   ```bash
   git init
   ```

3. **创建一个 README 文件**：

   ```bash
   echo "# 我的 Git 项目" > README.md
   ```

4. **添加文件到暂存区**：

   ```bash
   git add README.md
   ```

5. **提交更改**：

   ```bash
   git commit -m "初始化项目，添加 README 文件"
   ```

6. **查看提交历史**：

   ```bash
   git log
   ```

   **预期结果**：显示你刚刚的提交记录，包括提交信息和提交哈希值。

### 练习 2：创建和合并分支

通过这个练习，你将学习如何使用分支开发新功能，并将其合并到主分支。

**步骤**：

1. **创建一个新的分支**：

   ```bash
   git branch feature/add-login
   ```

2. **切换到新分支**：

   ```bash
   git checkout feature/add-login
   ```

   > **替代命令**（Git 2.23+）：

   ```bash
   git switch -c feature/add-login
   ```

3. **在新分支中创建一个文件**：

   ```bash
   echo "登录功能开发中..." > login.txt
   ```

4. **添加并提交更改**：

   ```bash
   git add login.txt
   git commit -m "添加登录功能开发说明"
   ```

5. **切换回主分支**：

   ```bash
   git checkout main
   ```

6. **合并新分支到主分支**：

   ```bash
   git merge feature/add-login
   ```

7. **查看文件是否合并成功**：

   ```bash
   cat login.txt
   ```

   **预期结果**：显示文件内容“登录功能开发中...”。

8. **删除已合并的分支**：

   ```bash
   git branch -d feature/add-login
   ```

### 练习 3：使用 GitHub 进行代码托管

通过这个练习，你将学习如何将本地仓库推送到 GitHub，并进行简单的协作。

**步骤**：

1. **创建一个新的 GitHub 仓库**：

   - 登录 [GitHub](https://github.com/)。
   - 点击右上角的“+”号，选择“New repository”。
   - 输入仓库名称（如 `my-git-project`），选择公开或私有，点击“Create repository”。

2. **将远程仓库添加到本地仓库**：

   在本地项目目录中，执行：

   ```bash
   git remote add origin https://github.com/你的用户名/my-git-project.git
   ```

   **示例**：

   ```bash
   git remote add origin https://github.com/zhangsan/my-git-project.git
   ```

3. **推送本地仓库到 GitHub**：

   ```bash
   git push -u origin main
   ```

   > **注意**：如果你的默认分支不是 `main`，请将 `main` 替换为相应的分支名。

4. **在 GitHub 上查看提交**：

   访问你的 GitHub 仓库页面，确认 `README.md` 和其他提交的文件是否已成功推送。

### 练习 4：解决合并冲突

通过这个练习，你将学习如何在 Git 中解决合并冲突。

**步骤**：

1. **创建并切换到新分支**：

   ```bash
   git checkout -b feature/edit-readme
   ```

2. **修改 `README.md` 文件**：

   打开 `README.md`，添加一行文本：

   ```markdown
   ## 添加了新的功能
   ```

3. **提交更改**：

   ```bash
   git add README.md
   git commit -m "在 README 中添加新的功能说明"
   ```

4. **切换回主分支**：

   ```bash
   git checkout main
   ```

5. **修改 `README.md` 文件**：

   打开 `README.md`，添加另一行文本：

   ```markdown
   ## 项目简介
   ```

6. **提交更改**：

   ```bash
   git add README.md
   git commit -m "在 README 中添加项目简介"
   ```

7. **尝试合并新分支到主分支**：

   ```bash
   git merge feature/edit-readme
   ```

8. **处理合并冲突**：

   Git 会提示 `README.md` 存在冲突。打开 `README.md`，你会看到类似如下的冲突标记：

   ```markdown
   ## 项目简介

   <<<<<<< HEAD
   ## 添加了新的功能
   =======
   ## 项目简介
   >>>>>>> feature/edit-readme
   ```

   **解决方法**：

   根据需要选择保留哪部分内容，或手动合并。例如：

   ```markdown
   ## 项目简介
   ## 添加了新的功能
   ```

9. **标记冲突已解决**：

   ```bash
   git add README.md
   ```

10. **完成合并提交**：

    ```bash
    git commit -m "解决 README 中的合并冲突"
    ```

11. **查看合并结果**：

    ```bash
    cat README.md
    ```

    **预期结果**：`README.md` 包含你手动合并的内容。

