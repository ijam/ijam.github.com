---
layout: post
title: "[Obj-c] Accessor Method"
date: 2012-04-11 00:06
comments: true
categories: Obj-c
---

宣告實體變數(iVar)，由於預設為protected，只能給自己或繼承者存取，若要給外部類別存取的話，則需使用accessor method來產生setter、getter。

    @interface Player: NSObject 
    {
      NSString *name; //宣告實體變數(iVar)
    }

    @property (nonatomic, retain) NSString *name;  //宣告setter、getter

    @synthesize name;  //根據property賦予的屬性(copy, retain等)實作setter、getter

如此ㄧ來，compiler會自動產生setter、getter：

    - (void)setName:(NSString *)theName;  //setter
    - (NSString *)name;   //getter

objective-c 2.0後，由於Dot Syntax的關係，[self name]即等於self.name，所以setter、getter傳統寫法為：

//setter

    [self setName:@"ijam"];
    
//getter

    [self name];

加入Dot Syntax後，

//setter

    self.name = @"ijam";
    
//getter

    NSLog(@"My name is: %@", self.name);

而self.name若有assign值的話，則會自動呼叫setter，
反之，則只呼叫getter，

利用iVar assign值也不會呼叫setter，而是直接賦予iVar值。

另外，也有看過在iVar前/後加上underscore的，然後再利用@synthesize property = iVar來自定accessor method name，這樣作法似乎是為了避免造成iVar與property的混淆，提高程式可讀性。

stackoverflow也有相關討論串，可參考[這邊](http://goo.gl/M1dNd)。

至於使用property時機？可參考[這邊](http://goo.gl/p0fam)。

