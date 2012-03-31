---
layout: post
title: "[iOS] Apple Push Notification service(APNs)"
date: 2012-04-01 01:50
comments: true
categories: iOS
---

推播服務在APP中是經常會使用到的功能，利用推播可以很容易的通知你的APP使用者某些訊息，如：APP有更新啥新玩意兒，由於可以自定sound或badge等的出現，可以增加曝光度、吸引使用者目光，在使用者ㄧ時手癢情況下，或許可以多增加些廣告收益(誤)。

好了，首先要先跟APNS註冊推播服務

    [[UIApplication sharedApplication] registerForRemoteNotificationTypes:
    UIRemoteNotificationTypeBadge | UIRemoteNotificationTypeSound | UIRemoteNotificationTypeAlert];

這段主要是要與APNS說你想使用推播，你可以自行選擇notification的types。

完成後，必須傳送device token等的相關資訊給你的provider(server)。token是必要的，因為APNs會利用token跟device做溝通，當然，你也可以傳送些額外的資訊。

    - (void)application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken
    {
      ...
    }

傳送過程中若有發生錯誤，會反應在底下這個method。

    - (void)application:(UIApplication *)application didFailToRegisterForRemoteNotificationsWithError:(NSError *)error
    {
      NSLog(@"The error is: %@", error);
    }

#####原因可能多半是

- 網路不通 or 在simulator執行
- AppID有問題
- Sandbox or Production環境不對

檢查下吧，再不行就dump出來看吧:p

基本上，這樣就可以接收來自server的推播了，local端若想玩玩的話，可以試試[PushMeBaby](https://github.com/stefanhafeneger/PushMeBaby)這套application。

參考來源：[官方](http://goo.gl/aQpwo)
