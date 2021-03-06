---
title: Élément CustomEntry pour CustomControl pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364068"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)

Fournit une définition du contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomEntry`. Vous devez spécifier les éléments affichés par la définition.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.|
|[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit les données affichées par le contrôle et leur mode d’affichage.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl pour la configuration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit les définitions du contrôle commun.|

## <a name="remarks"></a>Remarks

Dans la plupart des cas, une seule définition est requise pour chaque contrôle personnalisé commun, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl pour la configuration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
