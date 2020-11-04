
# Skype 历史记录导出器

**这是一个简单的脚本，主要用来导出Skype Version 8.0以上的版本,旧版本Skype 7.0及以下中main.db采用的sqlite数据结构，  
而8.0后不再支持采用了新的数据结构方式，用了Google 开源的 Level Db.**

`(Skype 采用了Electron框架的[浏览器] IndexedDB来作为数据库，他是一个Google开源的LevelDB数据库文件，里面保存着聊天记录，联系人列表的缓存记录)`
```bash
在Linux上他的路径为：
`~/.config/skypeforlinux/IndexedDB`
在Windows上他的路径为:
`%appdata%/Microsoft/Skype for Desktop/IndexedDB/file__0.indexeddb.leveldb`
```

但是Chrome使用了一个不是用JavaScript实现的自定义比较器(尽管这应该不是很难)


Tips:
作为一个快速的解决方案。

### 第①步：
我们可以使用Elecrtron的调试工具。按Ctrl+Alt+Shift+d，然后Ctrl+Alt+i。从Application选项卡找到Storage -> IndexedDB并记住数据库名称。For me it was `s4l-username`.

### 第②步:
接着，打开`export.js` 脚本并且将 `your-db-username-here` 这个字段替换成你自己的Skype的数据库名，也就是 `file__0.indexeddb.leveldb`,
然后打开控制台(Console)，并且把完整的 `export.js` 源码复制到控制台(Console)并且按回车执行代码，如果一切顺利的话，那么您将会得到一份Json格式
的所有聊天记录文件。

### 第③步:
你可以运行 `html.js` 脚本把 Json格式的文件转换成HTML,这样更加方便查看。
将Json文件拷贝到同目录下，然后运行 `node html.js` 执行JavaScript脚本，最后将会得到一份转换后的HTML文档，图片和视频、文件不包含在内。

> 感谢：
>> github上为数不多的skype聊天记录研究项目中的开源贡献者 - Siilike (资料上显示来自爱沙尼亚国)<br>
>> 个人主页 https://lauri.keel.ee/<br>
>> 开源项目地址 https://github.com/siilike/skypechatsexporter<>