---
layout: post
title: Jekyll中markdown中文显示行尾空格
author: Ruoshan Huang
---

markdown获得的`<p>`的内容是把换行直接换为空格了，英文没问题，但是中文就有很多不必要的空格。

查到的解决方法是这个链接[有格调地点我](http://chenyufei.info/blog/2011-12-23/fix-chinese-newline-becomes-space-in-browser-problem/)。

如链接的文章所说，这个在github page中不能用，因为gh不启用plugin。先对markdown做处理再提交就OK了。
具体的做法如下：

    \#!/usr/bin/env ruby
    \# encoding: UTF-8
    \# preprocessing the text for markdown writen in Chinese

    han = '\p{Han}|[，。？；：‘’“”、！……（）]'
    ChineseRegex = /(#{han}) *\n *(#{han})/m

    ARGV.each do |fn|
        lines = ''
        File.open(fn,'r') do |file|
            lines = file.gets(nil)
            lines.gsub!(ChineseRegex,'\1\2')
        end
        File.open(fn,'w') do |file|
            file.write(lines)
        end
    end
