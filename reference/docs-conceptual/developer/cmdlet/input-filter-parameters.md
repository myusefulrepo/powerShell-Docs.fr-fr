---
title: Paramètres de filtre d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364388"
---
# <a name="input-filter-parameters"></a>Paramètres de filtre d’entrée

Une applet de commande peut définir des paramètres `Filter`, `Include`et `Exclude` qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.

En règle générale, l’ensemble d’objets d’entrée est spécifié par un paramètre `InputObject`, `Path`ou `Name`. Par exemple, une applet de commande peut avoir un paramètre `Path` qui accepte plusieurs chemins d’accès à l’aide de caractères génériques, et chaque chemin d’accès pointe vers un objet d’entrée. Utilisés ensemble, les paramètres `Filter`, `Include`et `Exclude` qualifieront davantage les chemins d’accès de l’applet de commande à chaque fois qu’elle est appelée.

## <a name="include-and-exclude-parameters"></a>Paramètres include et Exclude

Les paramètres `Include` et `Exclude` identifient les objets qui sont inclus ou exclus de l’ensemble d’objets d’entrée transmis à l’applet de commande. Utilisez ces paramètres lorsque le filtre peut être exprimé dans le langage générique standard. (Pour plus d’informations sur les caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.) Le paramètre `Include` comprend tous les objets dont les noms correspondent au filtre d’inclusion. Le paramètre `Exclude` exclut tous les objets dont les noms correspondent au filtre.

## <a name="filter-parameter"></a>Paramètre de filtre

Le paramètre `Filter` spécifie un filtre qui n’est pas exprimé dans le langage générique standard. Par exemple, les interfaces de service Active Directory (ADSI) ou les filtres SQL peuvent être passés à l’applet de commande par le biais de son paramètre `Filter`. Dans les applets de commande fournies par Windows PowerShell, ces filtres sont spécifiés par les fournisseurs Windows PowerShell qui utilisent l’applet de commande pour accéder à un magasin de données. Chaque fournisseur définit généralement son propre filtre.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrage si aucun jeu d’objets d’entrée n’est spécifié

Si aucun jeu d’objets d’entrée n’est spécifié, cela signifie généralement que vous filtrez par rapport à tous les objets. Pour plus d’informations, consultez la rubrique[obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)