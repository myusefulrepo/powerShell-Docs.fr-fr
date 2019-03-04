---
title: Exemple de Code RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854035"
---
# <a name="runspace06-code-sample"></a>Exemple de code RunSpace06

Voici le code source pour l’exemple Runspace06 décrit dans [configuration d’une instance d’exécution à l’aide un Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Cet exemple d’application crée une instance d’exécution basée sur un composant logiciel enfichable Windows PowerShell, qui est ensuite utilisé pour exécuter un pipeline avec une seule commande. Pour ce faire, l’application crée les informations de configuration d’instance d’exécution, crée une instance d’exécution, crée un pipeline avec une seule commande, puis exécute le pipeline.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (runspace06.cs) en utilisant le Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Vous pouvez télécharger le C# le fichier source (runspace06.cs) en utilisant le Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)