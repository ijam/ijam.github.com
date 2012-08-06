---
layout: post
title: "[fixed] CorePlot failed to build in XCode4.4"
date: 2012-08-06 21:47
comments: true
categories: fixed
---

升級Xcode4.4後，原本有使用CorePlot的projects，build後竟產生這樣的error

    clang: error: -Z-reserved-lib-stdc++: 'linker' input unused when '-c' is present
    
    Command /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/clang failed with exit code 1
    
原來是因為Xcode4.4將compiler升級到了LLVM 4.0

####解決辦法：

* [安裝新的CorePlot吧QQ](http://goo.gl/LeMny)

* 把compiler換成LLVM GCC

[參考資料1](http://goo.gl/xGmdj)

[參考資料2](http://goo.gl/D5fo1)

[stackoverflow討論](http://goo.gl/xlulp)