---
title: Éléments générés automatiquement de l’aide basée sur le commentaire | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a7098fe-0854-4fbb-83e9-073c20b299c7
caps.latest.revision: 4
ms.openlocfilehash: 4d8f2e9d4c5c38cc08d9114ad802ca9db34f9047
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856765"
---
# <a name="autogenerated-elements-of-comment-based-help"></a>Éléments générés automatiquement de l’aide basée sur les commentaires

Le `Get-Help` applet de commande génère automatiquement plusieurs éléments d’une rubrique en fonction du commentaire. Ces éléments générés automatiquement donnent aide basée sur un commentaire très similaire à l’aide qui est généré à partir de fichiers XML.

## <a name="autogenerated-elements"></a>Éléments générés automatiquement

Le `Get-Help` applet de commande génère automatiquement les éléments suivants d’une rubrique d’aide. Vous ne pouvez pas modifier directement ces éléments, mais dans de nombreux cas, vous pouvez modifier les résultats en modifiant la source de l’élément.

**Nom** section le nom d’une rubrique d’aide de fonction est effectuée à partir du nom de fonction dans la définition de fonction. Le nom d’une rubrique d’aide de script provient du nom du fichier de script. Pour modifier le nom ou sa mise en majuscules, modifiez la définition de fonction ou le nom de fichier de script.

**Syntaxe** section de la syntaxe de la rubrique d’aide est générée à partir de la liste des paramètres dans l’instruction Param de la fonction ou d’un script. Pour ajouter des détails à la syntaxe de la rubrique d’aide, telles que le type .NET Framework d’un paramètre, ajoutez le détail à la liste de paramètres. Si vous ne spécifiez pas un type de paramètre, le type « Object » est inséré en tant que la valeur par défaut.

**Liste de paramètres** section les paramètres de la rubrique d’aide est générée à partir de la liste des paramètres dans le script ou la fonction et à partir de la description que vous ajoutez à l’aide de la `.Parameters` mot clé ou des commentaires dans la liste de paramètres.

Paramètres apparaissent dans la section de paramètres dans l’ordre dans lequel ils apparaissent dans la liste de paramètres. L’orthographe et la mise en majuscules des noms de paramètre est également issu de la liste de paramètres ; Il n’est pas affectée par le nom de paramètre spécifié par le `.Parameter` mot clé.

**Paramètres communs** les paramètres communs sont ajoutés à la liste de syntaxe et les paramètres de la rubrique d’aide, même si elles n’ont aucun effet. Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).
Les paramètres communs sont ajoutés à la liste de syntaxe et les paramètres de la rubrique d’aide, même si elles n’ont aucun effet. Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

**Table d’attributs de paramètre** 
 `Get-Help` génère la table d’attributs de paramètre qui apparaît lorsque vous utilisez le paramètre intégral ou paramètre de `Get-Help`. La valeur requis, la Position et la valeur par défaut des attributs de valeur provient de la syntaxe de fonction ou un script.

**Remarques** section de la section Notes de la rubrique d’aide est générée automatiquement à partir du nom de fonction ou un script. Vous ne pouvez pas modifier ou affectent son contenu.