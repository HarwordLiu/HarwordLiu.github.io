---
layout: post
title: 关于iOS选取相册中iCloud云上图片和视频 - HarwordLiu
date: 2017-07-05 15:02:35 +0800
categories: iOS

---

工作原因，需要处理接入一个视频模块，在视频选择的时候遇到了一个不太容易发现的bug，
产生的原因是由于手机内存小，而用户又打开了相册同步iCloud，

![](http://orsg2lmcy.bkt.clouddn.com/IMG_3120.PNG/600)

加载中的图片

![](http://orsg2lmcy.bkt.clouddn.com/IMG_3128.jpg/600)

在这时，如果本地可用内存过小，会导致
将本地相册中的图片或视频删除只留缩略图，如果App调用的时候想要选取这种图片就需要从iCloud云中进行下载，
才能获取原图或原视频。

**下面po下解决方案：**

如果你之前处理过相册问题，那么对如下的代码肯定不陌生，就是很普通的两个系统级别的请求回调，获取对应的图片，视频。

```
// get Image
[[PHImageManager defaultManager] requestImageDataForAsset:asset options:nil resultHandler:^(NSData * _Nullable imageData, NSString * _Nullable dataUTI, UIImageOrientation orientation, NSDictionary * _Nullable info) {

}];
// get Video
[[PHImageManager defaultManager] requestPlayerItemForVideo:asset options:nil resultHandler:^(AVPlayerItem * _Nullable playerItem, NSDictionary * _Nullable info) {
    if (completion) completion(playerItem,info);
}];
```

但是往往之前没有注意到第二个输入 `options` 是用来干嘛的，
其实解决方案就来自于这个 `PHImageRequestOptions`，`PHVideoRequestOptions`。

这这两个 `options` 都有一个共同的参数就是

```
@property (nonatomic, assign, getter=isNetworkAccessAllowed) BOOL networkAccessAllowed;
// if necessary will download the image from iCloud (client can monitor or cancel using progressHandler). Defaults to NO (see start/stopCachingImagesForAssets)
```

系统的解释也很详细，如果赋值 `YES` ，那么允许从 `iCloud` 中获取图片和视频，默认是 `NO`。

虽然这个问题解决不是很难，但是往往容易被忽略，所以记录一下。

这里非常感谢[@半迟尘](http://www.cnblogs.com/tanzhenblog/)大大的[TZImagePickerController](https://github.com/banchichen/TZImagePickerController)的源码，这个是一个非常靠谱的相册选择图片视频的库，并且处于仍在维护中。感兴趣的可以链接过去看一看源码，写的很好。

下面po一下完整的这个问题的解决代码：

```
/// Get Video
- (void)getVideoOutputPathWithAsset:(PHAsset *)asset completion:(void (^)(NSString *outputPath))completion {
    PHVideoRequestOptions* options = [[PHVideoRequestOptions alloc] init];
    options.version = PHVideoRequestOptionsVersionOriginal;
    options.deliveryMode = PHVideoRequestOptionsDeliveryModeAutomatic;
    options.networkAccessAllowed = YES;
    [[PHImageManager defaultManager] requestAVAssetForVideo:asset options:options resultHandler:^(AVAsset* avasset, AVAudioMix* audioMix, NSDictionary* info){
        // NSLog(@"Info:\n%@",info);
        AVURLAsset *videoAsset = (AVURLAsset*)avasset;
        // NSLog(@"AVAsset URL: %@",myAsset.URL);
        [self startExportVideoWithVideoAsset:videoAsset completion:completion];
     }];
}
/// Get Image

- (PHImageRequestID)getPhotoWithAsset:(PHAsset *)asset photoWidth:(CGFloat)photoWidth completion:(void (^)(UIImage *, NSDictionary *, BOOL isDegraded))completion {

    PHAsset *phAsset = (PHAsset *)asset;
    CGFloat aspectRatio = phAsset.pixelWidth / (CGFloat)phAsset.pixelHeight;
    CGFloat pixelWidth = photoWidth * 2.0;
    CGFloat pixelHeight = pixelWidth / aspectRatio;
    CGSize imageSize = CGSizeMake(pixelWidth, pixelHeight);

    // 修复获取图片时出现的瞬间内存过高问题
    PHImageRequestOptions *option = [[PHImageRequestOptions alloc] init];
    option.resizeMode = PHImageRequestOptionsResizeModeFast;
    PHImageRequestID imageRequestID = [[PHImageManager defaultManager] requestImageForAsset:asset targetSize:imageSize contentMode:PHImageContentModeAspectFill options:option resultHandler:^(UIImage * _Nullable result, NSDictionary * _Nullable info) {
        BOOL downloadFinined = (![[info objectForKey:PHImageCancelledKey] boolValue] && ![info objectForKey:PHImageErrorKey]);
        if (downloadFinined && result) {
            if (completion) completion(result,info,[[info objectForKey:PHImageResultIsDegradedKey] boolValue]);
        }
        // Download image from iCloud / 从iCloud下载图片
        if ([info objectForKey:PHImageResultIsInCloudKey] && !result) {
            PHImageRequestOptions *option = [[PHImageRequestOptions alloc]init];
            option.networkAccessAllowed = YES;
            option.resizeMode = PHImageRequestOptionsResizeModeFast;
            [[PHImageManager defaultManager] requestImageDataForAsset:asset options:option resultHandler:^(NSData * _Nullable imageData, NSString * _Nullable dataUTI, UIImageOrientation orientation, NSDictionary * _Nullable info) {
                UIImage *resultImage = [UIImage imageWithData:imageData scale:0.1];
                if (completion) completion(resultImage,info,[[info objectForKey:PHImageResultIsDegradedKey] boolValue]);

            }];
        }
    }];
    return imageRequestID;
}
```
