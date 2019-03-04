---
title: Le Test d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854735"
---
# <a name="how-to-test-updatable-help"></a>Guide pratique pour tester l’aide actualisable

Cette rubrique décrit les approches de test de l’aide actualisable pour un module.

## <a name="using-verbose-to-detect-errors"></a>À l’aide détaillée pour détecter les erreurs

Après avoir téléchargé le fichier XML HelpInfo et les fichiers CAB pour votre module, les fichiers de test en exécutant un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) commande avec le **Verbose** paramètre. Le **Verbose** paramètre dirige `Update-Help` pour signaler les étapes critiques dans ses actions, de lire le **HelpInfoUri** clés dans le manifeste de module pour valider les types de fichiers dans le fichier CAB décompressé et placer les fichiers dans le répertoire de module spécifique au langage.
Après avoir téléchargé le fichier XML HelpInfo et les fichiers CAB pour votre module, les fichiers de test en exécutant un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) commande avec le **Verbose** paramètre. Le **Verbose** paramètre dirige `Update-Help` pour signaler les étapes critiques dans ses actions, de lire le **HelpInfoUri** clés dans le manifeste de module pour valider les types de fichiers dans le fichier CAB décompressé et placer les fichiers dans le répertoire de module spécifique au langage.

Quand tous les messages documentés sont résolues, exécutez une `Update-Help` commande avec le **déboguer** paramètre. Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide actualisable.