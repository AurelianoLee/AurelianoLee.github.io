---
title: "Oh My Zsh Install"
weight: 2
bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
createDate: "2025-05-12"
updateDate: "2025-05-12"
---

# Oh My Zsh Install

- Date: 2025-05-12

## oh-my-zsh 介绍

- Github: [oh-my-zsh-github](https://github.com/ohmyzsh/ohmyzsh)

## MacOS

### zsh 安装并设为默认 shell

检查 zsh 是否为默认 shell。

```shell
# 查看当前的shell，如果不是/bin/zsh，需要修改
$ echo $SHELL
/bin/zsh

# 查看安装路径
$ echo $(which zsh)
/bin/zsh

# 设置
$ chsh -s $(which zsh)

# 检查-需要关闭终端重新打开后生效
$ echo $SHELL
/bin/zsh
```

### 安装oh-my-zsh

#### 安装

| Method    | Command                                                                                           |
| :-------- | :------------------------------------------------------------------------------------------------ |
| **curl**  | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **wget**  | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`   |
| **fetch** | `sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |

如果出现安装失败的问题，可能需要科学上网，或者使用 `oh-my-zsh` 提供的其他镜像：

| Method    | Command                                           |
| :-------- | :------------------------------------------------ |
| **curl**  | `sh -c "$(curl -fsSL https://install.ohmyz.sh/)"` |
| **wget**  | `sh -c "$(wget -O- https://install.ohmyz.sh/)"`   |
| **fetch** | `sh -c "$(fetch -o - https://install.ohmyz.sh/)"` |

#### 配置文件

配置文件在 `~/.zshrc` 下。

##### 插件

1. [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

    克隆仓库
    ```shell
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```

    添加到`~/.zshrc`下：
    ```
    plugins=(
        git
        zsh-autosuggestions
    )
    ```
2. [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

    `zsh-syntax-highlighting`作者更推荐使用手动安装的方式。
    ```shell
    # 下载插件
    brew install zsh-syntax-highlighting

    # 添加到.zshrc末尾
    echo "source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
    ```
3. [Incremental completion on zsh](https://mimosa-pudica.net/zsh-incremental.html)
   
    下载插件
    在`.oh-my-zsh/plugins/`下创建`incr`文件夹，将下载的插件复制到`incr`文件夹下。
    ```shell
    # 需要root权限
    sudo cp ~/Downloads/incr-0.2.zsh ~/.oh-my-zsh/plugins/incr/
    ```
4. [zsh-completions](https://github.com/zsh-users/zsh-completions)
    ```shell
    # 克隆仓库
    git clone https://github.com/zsh-users/zsh-completions.git ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions

    # 添加配置
    fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
    autoload -U compinit && compinit
    source "$ZSH/oh-my-zsh.sh"
    ```

##### 主题

[powerlevel10k](https://github.com/romkatv/powerlevel10k)

安装字体，详细安装步骤：[Step](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#meslo-nerd-font-patched-for-powerlevel10k)

```shell
# 克隆仓库
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"

# 可以使用gitee镜像
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

打开`.zshrc`，修改`ZSH_THEME`为`"powerlevel10k/powerlevel10k"`。

```shell
# 重启zsh，配置p10k
exec zsh
```
