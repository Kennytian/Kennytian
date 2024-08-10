## 如何使用国内源安装配置 Bun


### 国内安装源：
`curl -fsSL https://gitee.com/akirarika/bun-cn/raw/main/install.sh | bash -s 1.1.23`

### 国内更新源：
`curl -fsSL https://gitee.com/akirarika/bun-cn/raw/main/install.sh | bash -s 1.2.0`

### 检查生效：在`.bash_profile` 或 `.bashrc` 里添加如下

```bash
# bun
export BUN_INSTALL="$HOME/.bun" 
export PATH=$BUN_INSTALL/bin:$PATH
```

然后执行 `source ~/.bash_profile` 或 `source ~/.bashrc`

***如果还不生效，就 `vi /etc/profile`，添加上面的 export，然后 `source /etc/profile`***

### 加速镜像
在 ~ 目录下添加国内源，创建 `bunfig.toml` 文件，添加如下：
```toml
[install]
registry = "https://registry.npmmirror.com/"
```

***bunfig.toml 文件也可放在项目的根目录下，这样项目内使用 bun 命令时，会自动使用这个配置。***
