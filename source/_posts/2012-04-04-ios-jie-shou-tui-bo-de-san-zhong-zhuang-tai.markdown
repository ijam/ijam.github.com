---
layout: post
title: "[iOS] 接收推播的三種狀態"
date: 2012-04-04 16:43
comments: true
categories: iOS
---

完成推播註冊後，由server發送payload經由APNs到你的APP時，

主要會有三種狀態來處理你的推播資訊：

####APP正常運行或背景執行時：

主要都是利用這個method做處理，只是需要經過ㄧ些判斷。

如：

    - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo
    {
      if (nil == userInfo) {
        return;
      }
      
      NSDictionary *notification = userInfo;
      
      if (isBackground_) {
        //由背景執行開啟
      } else {
        //正常情況
      }
    }
    

####APP關閉時：

此時APP是未開啓狀態，如果先前已有對此APP開啟推播通知，那麼藉由推播通知開啟APP時，就會觸發以下method，你可以利用launchOptions來處理你的推播資訊。

如：

    - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
    {
      if (nil != launchOptions) {
        NSDictionary *notification = [launchOptions objectForKey:UIApplicationLaunchOptionsRemoteNotificationKey];
        ...
      }
    }
    
以上都是需要經由推播通知進入App，如果不理通知再自行進入App則不會發生以上情況。

done..
