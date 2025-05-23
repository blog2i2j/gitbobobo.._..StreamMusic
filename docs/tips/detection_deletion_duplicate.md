---
sidebar_position: 2
---

# 重复歌曲的检测与删除 {#detect}

随着曲库的增加，不可避免的会出现重复歌曲，这对于强迫症患者来讲简直太折磨了，遇到喜欢的歌曲都不知道该收藏哪个版本。

在音流中通过[媒体库模式](../guides/sync_mode#library-mode)连接并完全同步了服务端的数据后，在歌手详情页中，如果该歌手的歌曲存在重复项目，则会有**重复歌曲检测**功能的入口。

进入后即可按歌曲查看与其重复的各个版本，之后便可以根据页面的一些提示信息删除重复歌曲了。

:::info 开发者注

媒体库模式在曲库较大时体验不佳，建议仅在需要使用部分功能时切换，平时用直连模式就行。

:::

但这里有个问题，如果[连接的服务端不支持删除文件](../services#comparison)那该怎么办呢？

第一个解决办法，如果音流获取到的歌曲路径是真实路径，则可以复制页面中的删除命令，在其他软件中通过 SSH 连接并执行命令即可。

这样做的步骤比较复杂，还需要跨软件或跨设备操作，并不是特别好的做法。

第二个解决办法就是类似[前文](./focus_specific_audio)中的做法，通过 Docker 新建一个支持文件删除接口的服务端，在需要检测重复歌曲时，就通过音流切换到这个服务端，完整同步一遍数据之后操作即可。
