---
title: "使用具有多个版本的资源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: a3f2cf37eb185124d73443bbe42b5fcc82034f15
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="using-resources-with-multiple-versions"></a>使用具有多个版本的资源

> 适用于：Windows PowerShell 5.0

在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。 这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。

## <a name="installing-multiple-resource-versions-side-by-side"></a>并行安装多个资源版本

可以使用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet 的 **MinimumVersion**、**MaximumVersion** 和 **RequiredVersion** 参数来指定要安装的模块版本。 调用 **Install-Module** 而不指定某个版本安装最新版本。

例如，存在多个版本的 **xFailOverCluster** 模块，其中每个都包含 **xCluster** 资源。 调用 **Install-Module** 而不指定版本号的结果如下：

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

现在，如果再次调用 **Install-Module**，但指定 1.1.0.0 的 **RequiredVersion**，则结果如下：

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>在配置中指定资源版本

如果已在计算机上安装多个资源，那么在配置中使用资源时，必须指定该资源的版本。 为此，请指定 **Import-DscResource** 关键字的 **ModuleVersion** 参数。 如果你无法指定已安装多个版本的资源模块的版本，则配置会生成错误。

下面的配置演示如何指定要调用的资源的版本：

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>注意：Import-DscResource 的 ModuleVersion 参数在 PowerShell 4.0 中不可用。 在 PowerShell 4.0 中，你可以将模块规范对象传递到 Import-DscResource 的 ModuleName 参数，从而指定模块版本。 模块规范对象是包含 ModuleName 和 RequiredVersion 键的哈希表。 例如：

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

此操作在 PowerShell 5.0 中也有效，但建议使用 **ModuleVersion** 参数。

## <a name="see-also"></a>另请参阅
* [DSC 配置](configurations.md)
* [DSC 资源](resources.md)

