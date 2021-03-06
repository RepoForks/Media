# Media
Cross platform library to click pictures using camera, pick media files(photo, video and audio) from gallery and pick document/file from device

First install package from nuget using following command -
## Install-Package Xamarians.Media

You can integrate media tools in Xamarin Form application using following code:

 Shared Code -
 
Camera:-
 
```c#
using Xamarians.Media;

...

private string GenerateFilePath()
        {
			return Path.Combine(MediaService.Instance.GetPublicDirectoryPath(), MediaService.Instance.GenerateUniqueFileName("jpg"));
        }
		
string filePath = GenerateFilePath();
            var result = await MediaService.Instance.TakePhotoAsync(new CameraOption()
            {
                FilePath = filePath,
                MaxWidth = 300,
                MaxHeight = 300
            });
		
```
Photo Picker:- 
 
```c#
using Xamarians.Media;

...

var result = await MediaService.Instance.OpenMediaPickerAsync(MediaType.Image);

```
Video Picker:- 
 
```c#
using Xamarians.Media;

...

 var result = await MediaService.Instance.OpenMediaPickerAsync(MediaType.Video);
 
```
Audio Picker:-

```c#
using Xamarians.Media;

...

 var result = await MediaService.Instance.OpenMediaPickerAsync(MediaType.Audio);

```

File Picker:-
```c#
using Xamarians.Media;

...

 var result = await MediaService.Instance.OpenMediaPickerAsync(MediaType.Documents);

```
 Resize Image:-
 
 ```c#
using Xamarians.Media;

...
private string GenerateFilePath()
        {
			return Path.Combine(MediaService.Instance.GetPublicDirectoryPath(), MediaService.Instance.GenerateUniqueFileName("jpg"));
        }
		
 var result = await MediaService.Instance.OpenMediaPickerAsync(MediaType.Image);
            string resizeFilePath = GenerateFilePath();
            var success = await MediaService.Instance.ResizeImageAsync(result.FilePath, resizeFilePath, 250, 250);

```
Android - in MainActivity file write below code -
```c#
 Xamarians.Media.Droid.MediaServiceAndroid.Initialize();
```

iOS - in AppDelegate file write below code -
```c#
Xamarians.Media.iOS.MediaServiceIOS.Initialize();
```
The following permissions are needed in iOS -
```
NSCameraUsageDescription	
NSPhotoLibraryUsageDescription
NSMicrophoneUsageDescription
TCCServiceMediaLibrary
NSAppleMusicUsageDescription
```
In ios, for using file picker, you must create an App ID and provisioning profile. Then enable the iCloud service you want to use in following App ID.
After that you need to add Entitlement keys:- iCloud document storage, CloudKit in Entitlements.pList

