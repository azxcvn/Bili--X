本项目完全复刻自：https://github.com/BiliRoamingX/BiliRoamingX

## 使用方法


1. 下载本仓库源码到本地。
2. 下载合适版本的 `revanced-cli.jar`。
3. 使用支持 Gradle 的 IDE打开本项目根目录。
4. 构建产物：
	- 构建 `patches.jar`
	- 构建 `integrations.apk`

5. 将构建好的 `patches.jar`、`integrations.apk`、下载的 `revanced-cli.jar` 以及哔哩哔哩安装包放在同一个文件夹下。记得将安装包名称修改为bilibili.apk。

## 构建小技巧

- 仅适配 bilibili 国际版 3.20.4 及以下版本，请不要用于更高版本。
- 请务必使用 **JDK 11** 进行构建和注入
- 如果你还是没看懂，请直接查看原项目：https://github.com/BiliRoamingX/BiliRoamingX；如果你在编译中遇到了任何报错，请将错误发送给 AI 进行分析。

致谢：https://github.com/BiliRoamingX/BiliRoamingX

<details>
<summary>构建与注入命令示例（点击展开）</summary>


```shell
# 在项目根目录执行（Windows 使用 gradlew.bat）

# 同时构建 patches.jar 和 integrations.apk（推荐）
./gradlew dist

# 只构建 patches.jar
./gradlew :patches:dist

# 只构建 integrations.apk（发布版）
./gradlew :integrations:app:assembleRelease

# 使用 JDK 11 的 java 执行注入

# Windows 示例（假设 JDK 11 安装在 C:\Program Files\Java\jdk-11）
"C:\\Program Files\\Java\\jdk-11\\bin\\java.exe" -jar revanced-cli.jar \
	patch --merge integrations.apk \
	--patch-bundle patches.jar \
	--signing-levels 1,2,3 \
	bilibili.apk

# 或先将 JAVA_HOME 指向 JDK 11，再使用：
# %JAVA_HOME%\bin\java -jar revanced-cli.jar ...
```

</details>
