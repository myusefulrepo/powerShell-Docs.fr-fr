---
title: Exemples de Code GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855445"
---
# <a name="getproc04-code-samples"></a>Exemples de code GetProc04

Voici les exemples de code pour l’applet de commande GetProc04 exemple. Il s’agit du `Get-Process` exemple d’applet de commande décrites dans [ajoutant les rapports d’erreurs à votre applet de commande](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Cela `Get-Process` applet de commande appelle le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations de processus.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

Pour l’exemple de code complet, consultez les rubriques suivantes.

|Langue|Rubrique|
|--------------|-----------|
|C#|[GetProc04 (C#) exemple de Code](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 exemple de Code (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)