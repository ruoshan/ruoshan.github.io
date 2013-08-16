---
layout: post
title: A handy script for auto update markdown file to html.
author: Ruoshan Huang
date: 2013-08-16 10:37
---
## a handy script
to auto generate markdown to html everytime I update the markdown file,
and preview in Firefox. I wrote this scipt as followed,

{% highlight sh %}
#!/bin/bash
# a handy script to regenerate the markdown file once modified.
# please install the inotify-tools.
# USAGE:
#   cd to_your_directory
#   bash imarkdown.sh
#
# by Ruoshan Huang

while true
do
    f=`inotifywait -q -e modify --format "%w" *.markdown`
    html=${f/%markdown/html}
    echo "markdown generated: ${html}"
    markdown $f > $html
done
{% endhighlight %}

<br/>

## requirement
please install these softs first:
- `sudo apt-get install inotify-tools markdown`
- for Firefox, please install the [Auto Reload addon](https://addons.mozilla.org/en-US/firefox/addon/auto-reload/)
