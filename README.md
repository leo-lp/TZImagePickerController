# TZImagePickerController
[![CocoaPods](https://img.shields.io/cocoapods/v/TZImagePickerController.svg?style=flat)](https://github.com/banchichen/TZImagePickerController)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)


 A clone of UIImagePickerController, support picking multiple photos、original photo、video, also allow preview photo and video, support iOS6+.   
 一个支持多选、选原图和视频的图片选择器，同时有预览功能，支持iOS6+。
 
 ## 重要提示1：提issue前请先搜索，先从已有issue里找找线索。如果发现bug，请先和Demo对照自查下，如果Demo也有bug，请再提issue。Demo正常你那不正常的，提issue时请贴上你的初始化代码，注明必要的复现步骤。这样能避免多余的沟通，帮助你更快获取答案。
 
 ## 重要提示2：1.9.0版本后移除了"prefs:root="的调用，这个API已经被列为私有API，请大家尽快升级。目前最新版本2.1.6
 
     关于升级iOS10和Xcdoe8的提示:    
 在Xcode8环境下将项目运行在iOS10的设备/模拟器中，访问相册和相机需要额外配置info.plist文件。分别是Privacy - Photo Library Usage Description和Privacy - Camera Usage Description字段，详见Demo中info.plist中的设置。
    
     项目截图 1.Demo首页 2.照片列表页 3.照片预览页 4.视频预览页
<img src="https://github.com/banchichen/TZImagePickerController/blob/master/TZImagePickerController/ScreenShots/DemoPage.png" width="40%" height="40%"><img src="https://github.com/banchichen/TZImagePickerController/blob/master/TZImagePickerController/ScreenShots/photoPickerVc.PNG" width="40%" height="40%">
<img src="https://github.com/banchichen/TZImagePickerController/blob/master/TZImagePickerController/ScreenShots/photoPreviewVc.PNG" width="40%" height="40%"><img src="https://github.com/banchichen/TZImagePickerController/blob/master/TZImagePickerController/ScreenShots/videoPlayerVc.PNG" width="40%" height="40%">

## 一. Installation 安装

#### CocoaPods
> pod 'TZImagePickerController'

#### Carthage
> github "banchichen/TZImagePickerController"

#### 手动安装
> 将TZImagePickerController文件夹拽入项目中，导入头文件：#import "TZImagePickerController.h"

## 二. Example 例子

    TZImagePickerController *imagePickerVc = [[TZImagePickerController alloc] initWithMaxImagesCount:9 delegate:self];
    
    // You can get the photos by block, the same as by delegate.
    // 你可以通过block或者代理，来得到用户选择的照片.
    [imagePickerVc setDidFinishPickingPhotosHandle:^(NSArray<UIImage *> *photos, NSArray *assets) {
    
    }];
    [self presentViewController:imagePickerVc animated:YES completion:nil];
  
## 三. Requirements 要求
   iOS 6 or later. Requires ARC  
   iOS6及以上系统可使用. ARC环境.
   
   When system version is iOS6 or iOS7,  Using AssetsLibrary.  
   When system version is iOS8 or later, Using PhotoKit.  
   如果运行在iOS6或7系统上，用的是AssetsLibrary库获取照片资源。  
   如果运行在iOS8及以上系统上，用的是PhotoKit库获取照片资源。
   
## 四. More 更多 

  If you find a bug, please create a issue.  
  Welcome to pull requests.  
  More infomation please view code.  
  如果你发现了bug，请提一个issue。 
  欢迎给我提pull requests。  
  更多信息详见代码，也可查看我的博客: [我的博客](http://www.jianshu.com/p/1975411a31bb "半尺尘 - 简书")
  
      关于issue: 
  请尽可能详细地描述**系统版本**、**手机型号**、**库的版本**、**崩溃日志**和**复现步骤**，**请先更新到最新版再测试一下**，如果新版还存在再提~如果已有开启的类似issue，请直接在该issue下评论说出你的问题
  
## 五. Other 其它    

      常见问题
**Q：pod search TZImagePickerController 搜索出来的不是最新版本**       
A：需要在终端执行cd转换文件路径命令退回到Desktop，然后执行pod setup命令更新本地spec缓存（可能需要几分钟）,然后再搜索就可以了       
     
**Q：拍照后照片保存失败**         
A：请参考issue481：https://github.com/banchichen/TZImagePickerController/issues/481 的信息排查，若还有问题请直接在issue内评论   
 
**Q：photos数组图片不是原图，如何获取原图？**        
A：请参考issue457的解释：https://github.com/banchichen/TZImagePickerController/issues/457    

**Q：系统语言是中文/英文，界面上却有部分相册名字、返回按钮显示成了英文/中文？**        
A：请参考issue443的解释：https://github.com/banchichen/TZImagePickerController/issues/443
 
**Q：预览界面能否支持传入NSURL、UIImage对象？**       
A：排期中，优先级高   

**Q：可否支持横屏？**        
A：1.8.4版本已支持    

**Q：可否加入视频拍摄功能？**      
A：排期中，优先级中   

**Q：可否加入视频多选功能？**         
A：1.8.4版本已支持   

**Q：可否让视频和图片允许一起选？**         
A：1.8.4版本已支持   
  
**Q：可否增加微信编辑图片的功能？**           
A：考虑下，优先级低  

      最近更新    
2.1.6 新增allowCameraLocation属性，默认为YES，置为NO时不会在照相/摄像时定位，修复一个序号紊乱的bug              
2.1.5 修复开启showSelectedIndex后照片列表页iCloud图片进度条紊乱的bug              
2.1.4 新增多个页面和组件的样式自定义block，允许自定义绝大多数UI样式              
2.1.2 新增showPhotoCannotSelectLayer属性，当已选照片张数达到最大可选张数时，可像微信一样让其它照片显示一个提示不可选的浮层            
2.1.1 新增是否显示图片选中序号的属性，优化一些细节                 
2.1.0.3 新增拍摄视频功能，优化一些细节           
2.0.1 修复一些bug        
2.0.0.6 优化自定义languageBundle的支持，加入使用示例       
2.0.0.5 优化性能，提高选择器打开速度，新增越南语支持    
2.0.0.2 新增繁体语言，可设置首选语言，国际化支持更强大；优化一些细节     
1.9.8  支持Carthage，优化一些细节    
1.9.6  优化视频预览和gif预览页toolbar在iPhoneX上的样式      
1.9.5  优化视频导出API，和其它一些细节     
1.9.4  适配iPhoneX       
1.9.0  移除"prefs:root="的调用，这个API已经被列为私有API，请大家尽快升级     
...   
1.8.4  加入横竖屏适配；支持视频/gif多选；支持视频和照片一起选    
1.8.1  新增2个代理方法，支持由上层来决定相册/照片的显示与否     
1.8.0  修复若干bug, 提升流畅度     
...   
1.7.7  支持GIF图片的播放和选择    
1.7.6  支持对共享相册和同步相册的显示     
1.7.5  允许不进入预览页面直接选择照片     
1.7.4  支持单选模式下裁剪照片，支持任意矩形和圆形裁剪框    
1.7.3  优化iCloud照片的显示与选择    
...   
1.5.0  可把拍照按钮放在外面；可自定义照片排序方式；Demo页的UI大改版，新增若干开关；   
...      
1.4.5  性能大幅提升（性能测试截图请去博客查看）；可在照片列表页拍照；Demo大幅优化；   
...        
