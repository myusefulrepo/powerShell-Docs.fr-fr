---
title: Exemple de code RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: a99d0cc0dd35ae4c1a52e3624a9dd5af2a26c97a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360138"
---
# <a name="runspace05-code-sample"></a>Exemple de code RunSpace05

Voici le code source de l’exemple Runspace05 décrit dans [configuration d’une instance d’exécution à l’aide de RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Cet exemple montre comment créer les informations de configuration de l’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une commande unique, puis exécuter le pipeline. La commande exécutée est l’applet de commande `Get-Process`.

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (runspace05.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)