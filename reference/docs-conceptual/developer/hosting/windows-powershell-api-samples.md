---
title: Exemples d’API Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360838"
---
# <a name="windows-powershell-api-samples"></a>Exemples d’API Windows PowerShell

Cette section comprend un exemple de code qui montre comment créer des instances d’exécution qui restreignent les fonctionnalités et comment exécuter de façon asynchrone des commandes à l’aide d’un pool d’instances d’exécution pour fournir le instances d’exécution. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

[Exemple PowerShell01](./windows-powershell01-sample.md) Cet exemple montre comment utiliser un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour limiter les fonctionnalités d’une instance d’exécution. La sortie de cet exemple montre comment limiter le mode de langage de l’instance d’exécution, comment marquer une applet de commande comme étant privée, comment ajouter et supprimer des applets de commande et des fournisseurs, ajouter une commande de proxy, et bien plus encore.

[Exemple PowerShell02](./windows-powershell02-sample.md) Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution. L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.