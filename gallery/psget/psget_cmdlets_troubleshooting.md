---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_cmdlets_troubleshooting
ms.technology: powershell
ms.openlocfilehash: 4758c650933b082f467c66ad4accb4c8a1fb514e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解决“警告: 无法下载包‘你的包名称’”问题？




据报告，Install-Module 或 Update-Module 在某些计算机上有时会失败。
根据我们的调查，此问题与网络连接有关。
最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。
你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。
下面，我们使用“Azure”模块作为示例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

