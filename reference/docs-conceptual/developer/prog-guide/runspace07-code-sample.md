---
title: Exemple de code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: f40b24951c44c228d85524845045aea58f680f2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870606"
---
# <a name="runspace07-code-sample"></a>Exemple de code RunSpace07

Voici le code source de l’exemple Runspace07 décrit dans [création d’une application console qui ajoute des commandes à un pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).
Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, puis exécute le pipeline. Les commandes ajoutées au pipeline sont les applets de commande `Get-Process` et `Measure-Object`.

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (runspace07.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
