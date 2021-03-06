---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_update modulemanifest
ms.technology: powershell
ms.openlocfilehash: 85153872326c5af8f869bc2254040eca1a152f8b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="update-modulemanifest"></a>Update-ModuleManifest
更新模块清单文件。

## <a name="description"></a>说明

Update-ModuleManifest cmdlet 更新模块清单 (.psd1) 文件。

### <a name="notes"></a>注释
    - DscResourcesToExport 仅在最新的 PowerShell 5.0 版本上才受支持。 如果你正在较低版本的 PowerShell 上运行，我们将无法更新该字段。

## <a name="cmdlet-syntax"></a>Cmdlet 语法
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 联机帮助参考

[Update-ModuleManifest](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a>示例命令

此新的 cmdlet 用于通过输入属性值帮助更新清单文件。 它会接收 New-ModuleManifest 接收的所有参数。

我们注意到，许多模块作者想要在诸如 FunctionsToExport 和 CmdletsToExport 等导出值中指定“\*”。在将模块发布到 PowerShell 库期间，未指定的函数和命令将无法正确填充到库上。 因此，我们建议模块作者使用合适的值更新自己的清单。

如果你的模块已导出属性，Update-ModuleManifest 将使用来自导出函数、cmdlet、变量等中的信息填充指定的清单文件。
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

使用 Update-ModuleManifest 之后：
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

对于每个模块，还存在与之关联的元数据字段。 为了在 PowrShell 库中正确显示元数据，你可以使用 Update-ModuleManifest 在 PrivateData 下填充这些字段。

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

来自清单文件模板的 PrivateData 哈希表具有以下属性

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

