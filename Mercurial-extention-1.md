Mercurial の便利な Extention を利用する。 その１

Mercurial はシンプルな作りになっています。 
Git のように最初からいろいろとできません。
しかし、 Extention を利用することで、 hg コマンドを便利に利用できます。

### Extenton の使い方

Mercurial の Extention は、 hgrc で管理します。
利用したい Extention を [extentions] セクションで記述します。

例)

```
[extentions]
color =
graphlog =
```

### hg コマンドの結果に色を付ける

```.hgrc
[extentions]
color =
```

### ASCII アートのリビジョングラフと履歴を並べて表示する

```.hgrc
[extentions]
graphlog =
```

hg log を表示する際に、 ASCII アートのリビジョングラフを表示できるようになります。

```
$ hg log -G -l4
@    changeset:   4061:8ec0b3a74e79
|\   tag:         tip
| |  parent:      4060:b5fb711e85b9
| |  parent:      4059:0ae9f691fac2
| |  user:        shimizukawa <shimizukawa@gmail.com>
| |  date:        Sun Mar 17 10:58:28 2013 +0900
| |  summary:     merge heads
| |
| o  changeset:   4060:b5fb711e85b9
| |  parent:      4053:33577a5ee841
| |  user:        shimizukawa <shimizukawa@gmail.com>
| |  date:        Sun Mar 10 22:07:31 2013 +0900
| |  summary:     Add i18n capabilities for custom templates.
| |
o |  changeset:   4059:0ae9f691fac2
| |  user:        shimizukawa <shimizukawa@gmail.com>
| |  date:        Sun Mar 17 10:55:50 2013 +0900
| |  summary:     update CHANGES
| |
o |    changeset:   4058:bf8c420b9c9f
|\ \   parent:      4054:e5c218f45ec7
| | |  parent:      4057:fc66da28da18
| | |  user:        Takayuki Shimizukawa <shimizukawa+bitbucket@gmail.com>
| | |  date:        Sun Mar 17 10:50:28 2013 +0900
| | |  summary:     Merged in knzm/sphinx-fix-versionchange-fork (pull request #124)
| | |
```

style オプションで表示をコンパクトにできます。

```
$ hg log -G --style=compact -l4
@    4061[tip]:4060,4059   8ec0b3a74e79   2013-03-17 10:58 +0900   shimizukawa
|\     merge heads
| |
| o  4060:4053   b5fb711e85b9   2013-03-10 22:07 +0900   shimizukawa
| |    Add i18n capabilities for custom templates.
| |
o |  4059   0ae9f691fac2   2013-03-17 10:55 +0900   shimizukawa
| |    update CHANGES
| |
o |    4058:4054,4057   bf8c420b9c9f   2013-03-17 10:50 +0900   shimizukawa+bitbucket
|\ \     Merged in knzm/sphinx-fix-versionchange-fork (pull request #124)
| | |
```

