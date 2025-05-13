---
title: "Git 配置代理"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
createDate: "2025-05-13"
---

# Git 配置代理

- Date: 2025-05-13

## 设置代理

### 全局代理（不推荐）
```shell
#使用http代理 
git config --global http.proxy http://127.0.0.1:port
git config --global https.proxy https://127.0.0.1:port

#使用socks5代理
git config --global http.proxy socks5://127.0.0.1:port
git config --global https.proxy socks5://127.0.0.1:port
```

### 针对 Github 代理
```shell
#使用socks5代理（推荐）
git config --global http.https://github.com.proxy socks5://127.0.0.1:port

#使用http代理（不推荐）
git config --global http.https://github.com.proxy http://127.0.0.1:port
```

### 取消代理
```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```

## Ref

- [代理解决Github被墙](https://zhuanlan.zhihu.com/p/481574024)
