---
layout: post
title: "[iOS] 區別ios版本"
date: 2012-10-15 22:36
comments: true
categories: iOS
---

想在新版iOS SDK上使用新的功能又不能影響到原有的iOS舊版本程式架構，
常常需要針對不同的iOS版本做對應的處理。

* compile-time conditional : 在compile時，compiler會根據不同的設定值來確保其順利找到對應的code。

  * __IPHONE_OS_VERSION_MAX_ALLOWED : 根據Base SDK的設定。
  
  * __IPHONE_OS_VERSION_MIN_REQUIRED :根據iPhone OS Deployment Target的設定。

* run-time check : 可以利用 [[UIDevice currentDevice] systemVersion]來判斷使用者的iOS版本。



#####in project settings : 

* Base SDK : 你想要使用的功能，其iOS最高版本。(通常是設為最新的)
* iPhone OS Deployment Target : 還支援的iOS最低版本。

#####各iOS版本的對應 :

    #define __IPHONE_2_0     20000
    #define __IPHONE_2_1     20100
    #define __IPHONE_2_2     20200
    #define __IPHONE_3_0     30000
    #define __IPHONE_3_1     30100
	#define __IPHONE_3_2     30200
	#define __IPHONE_4_0     40000
	#define __IPHONE_4_1     40100
	#define __IPHONE_4_2     40200
	#define __IPHONE_4_3     40300
	#define __IPHONE_5_0     50000
	#define __IPHONE_5_1     50100
	#define __IPHONE_6_0     60000
	#define __IPHONE_NA      99999  /* not available */

#####example : 

    #if __IPHONE_OS_VERSION_MAX_ALLOWED >= 60000
      if (6.0 <= [[[UIDevice currentDevice] systemVersion] floatValue]) {
        // iOS 6.0 後的新功能
      }
    #else
      if (6.0 > [[[UIDevice currentDevice] systemVersion] floatValue]) {
        // iOS 6.0 以前的功能
      }
    #endif





