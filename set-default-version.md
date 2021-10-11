# set default version

複数のバージョンをインストールした際にデフォルトバージョンの設定方法

## macOS

- macOSでは常に最新バージョンがデフォルトバージョンとなる
- macOSで旧バージョンをデフォルトバージョンにする場合はシンボリックリンクの付け替えが必要

### シンボリックリンクの付け替え

#### Current

```
> cd /Library/Frameworks/Python.framework/Versions
> sudo ln -fsn 3.x Current
```

#### 各種ツール

- `python3-intel64` は `python 3.10` 以降

```
> cd /usr/local/bin
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/2to3 2to3
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/idle3 idle3
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/pip3 pip3
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/pydoc3 pydoc3
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/python3 python3
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/python3-config python3-config
> sudo ln -fsn ../../../Library/Frameworks/Python.framework/Versions/3.x/bin/python3-intel64 python3-intel64
```

### 環境変数

- `PATH` の変更

#### zsh

```
> vim ~/.zprofile
---------------------------------------------------------------------------------------------------
# Setting PATH for Python 3.x
# The original version is saved in .zprofile.pysave
PATH="/Library/Frameworks/Python.framework/Versions/3.x/bin:${PATH}"
export PATH

# Setting PATH for Python 3.xx
# The original version is saved in .zprofile.pysave
# PATH="/Library/Frameworks/Python.framework/Versions/3.xx/bin:${PATH}"    <-- コメントアウト
# export PATH                                                              <-- コメントアウト
---------------------------------------------------------------------------------------------------
```