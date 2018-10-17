---
title: Camera intrinsics
description: Provides information about camera intrinsics.
ms.author: windowsdriverdev
ms.date: 9/26/2018
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
---

# Camera intrinsics

A camera driver (or alternatively, through DMFT) can attach a camera intrinsics attribute to either a stream attribute store using [MFStreamExtension_PinholeCameraIntrinsics](https://docs.microsoft.com/windows/desktop/medfound/mfstreamextension-pinholecameraintrinsics), or attach to a media frame attribute store using [MFSampleExtension_PinholeCameraIntrinsics](https://docs.microsoft.com/windows/desktop/medfound/mfsampleextension-pinholecameraintrinsics). If it is attached to a stream attribute store, the values of the camera intrinsics does not change during camera streaming. If it is attached to a media frame attribute store, then the intrinsics value might change for every frame. 

For the above two attributes, the value must be a structure of type [MFPinholeCameraIntrinsics](https://docs.microsoft.com/windows/desktop/api/mfapi/ns-mfapi-_mfpinholecameraintrinsics), which reports a list of camera intrinsic models. Each entry in this list is with type [MFPinholeCameraIntrinsic_IntrinsicModel](https://docs.microsoft.com/windows/desktop/api/mfapi/ns-mfapi-_mfpinholecameraintrinsic_intrinsicmodel), containing a resolution (width/height), pinhole model, and [MFCameraIntrinsic_DistortionModel](https://docs.microsoft.com/windows/desktop/api/mfapi/ns-mfapi-_mfcameraintrinsic_distortionmodel) distortion model. 

When using **MFPinholeCameraIntrinsics** with a stream attribute store, this list must contains at least one, and possibly many intrinsic models. The system will pick the intrinsics model based on the actively streaming frame format by matching the width and height of the frames. If an exact match is found, the intrinsics will be used. Otherwise, the first intrinsics with the same aspect ratio will be used instead, for example, when the list contains two entries, 640x480 and 1920x1080, respectively. If streaming with a 1280x720 media format, the 1080p intrinsics will be used with proper scaling. 

When using **MFPinholeCameraIntrinsics** with a media frame attribute store, this list must contain exactly one intrinsics model with the same resolution as the frame resolution.