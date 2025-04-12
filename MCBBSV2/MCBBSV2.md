# MCBBSV2 整合包规范

> [!WARNING]
> 当前 MCBBS 已关闭，具体规范无迹可寻，可以具体参考各启动器的开源实现。

文件格式为 Zip，文件后缀为 `.zip`。

## 目录结构

整合包的文件夹目录结构如下：

```
Root/
├── overrides/
│   ├── config/          # 存放所有配置文件
│   ├── mods/           # 存放所有模组文件
│   ├── shaderpacks/    # 存放光影包
│   └── options.txt     # options.txt 文件
└── mcbbs.packmeta      # 整合包元数据文件
```

## `mcbbs.packmeta` 文件

```json
{
  "manifestType": "minecraftModpack",
  "manifestVersion": 2,
  "name": "一个测试整合包",
  "version": "1.0.0",
  "author": "宅魂Kill",
  "description": "这是一个用于测试的整合包",
  "fileApi": "https://dl.mcxk.net/update",
  "forceUpdate": true,
  
  "//origin": "发布页面，如果fileApi不存在，可从相关发布网站的API获取更新信息，暂未开放",
  "origin": [
    {
      "type": "mcbbs",
      "id": 1234
    }
  ],
  
  "addons": [
    {
      "id": "game",
      "version": "1.16.5"
    },
    {
      "id": "forge",
      "version": "36.1.4"
    }
  ],
  
  "//libraries": "这个可以暂时先不实现",
  "libraries": [
    {
      "name": "cn.skinme.skinme-loader",
      "fileName": "skinme-loader-local.jar",
      "hint": "local"
    }
  ],
  
  "files": [
    {
      "type": "addon",
      "path": "mods/OptiFine_1.16.5_HD_U_G7.jar",
      "hash": "2122bcecf60700aa27fafca0bab6533a4c3029ef",
      "force": true
    },
    {
      "type": "addon",
      "path": "mods/chat_heads_forge-0.2.0.jar",
      "hash": "8d8496d22bebc3e61c690908a10855df595b08cd",
      "force": true
    },
    {
      "type": "addon",
      "path": "resourcepacks/BetterLeaves.zip",
      "hash": "597162e704d74d82a442f6fbe34e4edc70557ead",
      "force": true
    },
    {
      "type": "addon",
      "path": "config/betterf3.toml",
      "hash": "8d8496d22bebc3e61c690908a10855df595b08cd",
      "force": true
    },
    {
      "//": "支持从CurseForge下载资源",
      "type": "curse",
      "projectID": 238222,
      "fileID": 3414898,
      "force": true
    }
  ],
  
  "//settings": "这部分配置遵循服务器上的配置，是否允许玩家自行添加资源文件",
  "settings": {
    "install_mods": false,
    "install_resourcepack": true
  },
  
  "//launchInfo": "启动信息，遵循服务器上配置文件设定，如果forceUpdate为false则可以只遵循本地的",
  "launchInfo": {
    "minMemory": 2048,
    "//supportJava": "支持的Java版本，该选项非强制，但需要警告玩家",
    "supportJava": [8, 9],
    "launchArgument": ["", ""],
    "javaArgument": ["", ""]
  },
  
  "serverInfo": {
    "authlibInjectorServer": "https://littleskin.cn/api/yggdrasil"
  },
  
  "//sandbox": "sandbox与antiCheating优先遵循服务器上配置文件的设定",
  "//sandbox_comment": "沙盒，用于反作弊安全方面的设定",
  "sandbox": {
    "allowedPath": [],
    "permissionsGranted": []
  },
  
  "//antiCheating": "反作弊核心，由启动器启动游戏前加载运行",
  "antiCheating": {
    "core": "",
    "hash": ""
  }
}
```

你可以下载 [TestModpack.zip](https://github.com/MCLF-CN/docs/tree/main/MCBBSV2/TestModpack.zip) 作为参考。
