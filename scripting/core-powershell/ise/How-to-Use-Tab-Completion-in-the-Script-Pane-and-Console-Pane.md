---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "如何在脚本窗格和控制台窗格中使用 Tab 自动补全"
ms.technology: powershell
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: f2eec644055c228dd1a16a2c20a09996666ca6e1
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>如何在脚本窗格和控制台窗格中使用 Tab 自动补全
在脚本窗格或在命令窗格中进行键入时，Tab 自动补全将提供自动帮助。 使用以下步骤来利用此功能：

## <a name="to-automatically-complete-a-command-entry"></a>自动完成命令输入
在命令窗格或脚本窗格中，键入命令的几个字符，然后按 TAB 以选择所需补全文本。 如果有多个项以你最初键入的文本开头，那么继续按 Tab，直到出现所需的项。 Tab 自动补全可以帮助键入 cmdlet 名、参数名、变量名、对象属性名或文件路径。

> [!NOTE]
> 在脚本窗格中，仅当你编辑 .ps1、.psd1 或 .psm1 文件时，按 TAB 才会自动完成命令。 在命令窗格中键入时，Tab 自动补全随时都起作用。

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>自动完成 cmdlet 参数输入
在命令窗格或脚本窗格中，键入 cmdlet 后跟一个破折号，然后按 TAB 键。

例如，键入 `Get-Process -`，然后多次按 TAB 键以显示 cmdlet 的每个参数。

## <a name="see-also"></a>另请参阅
- [使用 Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [如何创建 PowerShell 选项卡](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

