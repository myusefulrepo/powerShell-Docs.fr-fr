---
title: Sans fin d’exécution erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853775"
---
# <a name="non-terminating-errors"></a>Erreur sans fin d’exécution

Cette rubrique décrit la méthode utilisée pour signaler les erreurs sans fin d’exécution. Elle explique également comment appeler la méthode à partir de l’applet de commande.

Lorsqu’une erreur sans fin d’exécution se produit, l’applet de commande doit signaler cette erreur en appelant le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode). Lors de l’applet de commande signale une erreur sans fin d’exécution, l’applet de commande peut continuer à fonctionner sur cet objet d’entrée et sur entrante supplémentaire objets du pipeline. Si l’applet de commande appelle le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode), l’applet de commande peut écrire un enregistrement d’erreur qui décrit la condition ayant provoqué l’erreur sans fin d’exécution. Pour plus d’informations sur les enregistrements d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).

Applets de commande peut appeler [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que nécessaire dans leurs méthodes de traitement des entrées. Toutefois, les applets de commande peut appeler [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) uniquement à partir du thread qui a appelé le [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode de traitement d’entrée. N’appelez pas [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir d’un autre thread. Au lieu de cela, communiquer des erreurs vers le thread principal.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell erreur enregistrements](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)