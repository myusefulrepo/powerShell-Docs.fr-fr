---
title: Arrêt des erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369328"
---
# <a name="terminating-errors"></a>Erreur avec fin d’exécution

Cette rubrique décrit la méthode utilisée pour signaler des erreurs de fin. Elle explique également comment appeler la méthode à partir de l’applet de commande et traite des exceptions qui peuvent être retournées par le runtime Windows PowerShell lorsque la méthode est appelée.

Lorsqu’une erreur se termine, l’applet de commande doit signaler l’erreur en appelant la méthode [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Cette méthode permet à l’applet de commande d’envoyer un enregistrement d’erreur qui décrit la condition à l’origine de l’erreur. Pour plus d’informations sur les enregistrements d’erreurs, consultez la page [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).

Lorsque la méthode [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) est appelée, le runtime Windows PowerShell arrête définitivement l’exécution du pipeline et lève une exception [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) . Toutes les tentatives ultérieures pour appeler [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)de commande. WriteError ou plusieurs autres API provoquent la levée d’une exception [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) par les appels.

L’exception [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) peut également se produire si une autre applet de commande du pipeline signale une erreur de fin, si l’utilisateur a demandé l’arrêt du pipeline, ou si le pipeline a été interrompu avant la fin pour une raison quelconque. L’applet de commande n’a pas besoin d’intercepter l’exception [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) , sauf si elle doit nettoyer les ressources ouvertes ou son état interne.

Les applets de commande peuvent écrire un nombre quelconque d’objets de sortie ou d’erreurs sans fin d’achèvement avant de signaler une erreur de fin. Toutefois, l’erreur d’arrêt interrompt définitivement le pipeline, et aucune sortie supplémentaire, les erreurs de fin ou les erreurs sans fin d’arrêt peuvent être signalées.

Les applets de commande peuvent appeler [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) uniquement à partir du thread qui a appelé la méthode de traitement d’entrée System. Management. Automation. cmdlet. [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)ou [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . N’essayez pas d’appeler [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) de commande. ThrowTerminatingError * ou [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir d’un autre thread. Au lieu de cela, les erreurs doivent être communiquées au thread principal.

Une applet de commande peut lever une exception dans son implémentation de la méthode System. [Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)ou [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Toute exception levée à partir de ces méthodes (à l’exception de quelques conditions d’erreur graves qui arrêtent l’hôte Windows PowerShell) est interprétée comme une erreur de fin qui arrête le pipeline, mais pas Windows PowerShell dans son ensemble. (Cela s’applique uniquement au thread principal de l’applet de commande. Exceptions non interceptées dans les threads générés par l’applet de commande, en général, arrêtez l’hôte Windows PowerShell.) Nous vous recommandons d’utiliser [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) au lieu de lever une exception, car l’enregistrement d’erreur fournit des informations supplémentaires sur la condition d’erreur, ce qui est utile pour l’utilisateur final. Les applets de commande doivent respecter les instructions du code managé par rapport à l’interception et à la gestion de toutes les exceptions (`catch (Exception e)`). Convertit uniquement les exceptions des types connus et attendus en enregistrements d’erreur.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
