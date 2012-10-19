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

* run-time check : 

  * 可以利用 [[UIDevice currentDevice] systemVersion] 判斷使用者的iOS版本。
  
  * 或是使用 - (BOOL)respondsToSelector:(SEL)aSelector 測試是否擁有可用的method或property，並可用 - (id)performSelector:(SEL)aSelector 避免compile時，因為某些被deprecated的method/property而產生error。

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
      } else {
        // iOS 6.0 前的功能
      }
      
    #else

      /* 
       * 假設older method是iOS 5.0中被deprecated的功能，
       * newer method是取代older的新功能，
       * 而compile環境是iOS 5.0，如果直接呼叫older的話，
       * build時就會出現warning，所以必須先測試older method是否可用，
       * 再使用performSelector呼叫，避免warning
       */

      if ([self respondsToSelector:@selector(newer:)]) {
      
        //代表使用者使用的是iOS 5.0以上，可以使用newer功能
        
        NSString *theNewMessage = [self performSelector:@selector(newer:) withObject:@"i'm newer"];
        
      } else {
      
        //代表newer不能用，則使用older
        
        NSString *theOldMessage = [self performSelector:@selector(older:) withObject:@"i'm older"];
      }
      
    #endif




