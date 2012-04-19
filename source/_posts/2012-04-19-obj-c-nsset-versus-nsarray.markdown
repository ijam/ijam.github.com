---
layout: post
title: "[Obj-c] NSSet versus NSArray"
date: 2012-04-19 23:17
comments: true
categories: Obj-c
---

####NSSet：

* 未排序的物件集合
* 確保物件唯一性
* 由於使用hash table的機制，所以在取得大量的物件時效能更好

    Performance Information:
    
    This performance information assumes adequate implementations for the hash method defined for the objects. 
    With a bad hash function, access and edits take linear time.

    * Accessing an element of a set takes constant time.
    * Setting and removing take constant time.

####NSArray：

* 經排序的物件集合
* 無唯一性
* 在寫入或取代資料內容時，效能較好

    Performance Information: 
    
    * Accessing an element of an array takes constant time.
    * Appending to and removing elements from either end take constant time.
    * Replacing an element takes constant time.
    * Inserting an element into the middle of an array takes linear time.

####結論：

搜尋大量的物件時，或是必須確保物件彼此間的唯一性時，使用NSSet;
普通的存取操作時，搜尋小量物件時，使用NSArray。

[資料來源](http://goo.gl/OVCTF)

[延伸閱讀](http://goo.gl/XFyzo)


