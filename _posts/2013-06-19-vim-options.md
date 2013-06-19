---
layout: post
title: vim的一些默认不打开但很有用的选项和功能
author: Ruoshan Huang
date: 2013-06-19 15:16
---

1. 关于补全，很多网上的推荐都是插件比如supertab之类的。我开始也使用，
   但是发现没原生的简单便捷。

    - 请先`:h ins-complete`.

    - 插入下的补全中要设置这几个变量，dictionary和path。dictionary是
      使用ctrl-x ctrl-k是使用的字典文件; path是ctrl-x ctrl-i是查找对应include
      头文件的位置。第一个相当于查字典，可以设置为`set dictionary="/usr/share/dict/words"`.
      第二个为想C这类语言补全常用函数库，可以设置为`set path+="/usr/include"`.
      设置后可以补全像printf(linux C 的各种接口)等的函数了。

    - 还有一个是不需要配置目录的(当然rtp还是要配的)，那就是omni complete，使用
      ctrl-x ctrl-o调用。这个补全必须打开`filetype on`和`filetype plugin on`.

2. `set scrolloff=5`这个设置是让光标移到倒数第5行的时候就开始滚动，浏览会比较舒服。

3. `set formatoptions+=nMtcq`和`set formatoptions-=l`这个设置可以对中文合并行
   以及自动换行有帮助，能去掉合并行时多余的空格等。帮助见`:h fo-table`.

4. `matchit.vim`这个插件包含在vim的runtime中，却没有被使用，它是对`%`命令的加强，
   不只对`{}[]<>()`等这类的块结构进行来回跳转，还能对`if...end(if)`的这样的结构进行跳转，
   这对于Ruby，LaTex这类语言来说非常方便。启用它只要把它从`/usr/share/vim/vim73/marcos/matchit.vim`
   中拷贝到你的`.vim/plugin/`中即可。

5. 暂时到这，想到再写。
