---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_pseditions
ms.technology: powershell
ms.openlocfilehash: fddac6b6741150a0d809dc434a7a14b646434e01
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="items-with-compatible-powershell-editions"></a>具有兼容 PowerShell 版本的项
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell 库提取支持的 PSEditions 元数据，并允许筛选兼容特定 PowerShell 版本的项

如果某个项已指定兼容的 PSEditions，则会在项显示页和项结果中将其显示为“PowerShell Editions”的一部分。
![具有 PSEditions 的项显示页](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>搜索在 PowerShellCore 上工作的库 UI 中的项
使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的项。

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。
![在结果中搜索兼容 Core PSEdition 的项](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。
![在结果中搜索兼容 Desktop PSEdition 的项](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>有关创作和查找兼容 PowerShell 版本的项的详细信息
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[PSEditions 模块](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[PSEditions 脚本](../psget/script/scriptwithpseditionsupport.md)

