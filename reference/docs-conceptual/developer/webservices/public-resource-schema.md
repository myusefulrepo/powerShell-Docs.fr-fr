---
title: Schéma de ressource publique | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366268"
---
# <a name="public-resource-schema"></a>Schéma des ressources publiques

La gestion OData utilise MOF pour définir les ressources et leurs propriétés. Les propriétés d’une entité de gestion OData correspondent directement aux propriétés du type managé retourné par l’applet de commande sous-jacente.

## <a name="defining-a-resource"></a>Définition d’une ressource

Chaque ressource correspond à un objet retourné par une applet de commande Windows PowerShell. Dans le fichier MOF des ressources publiques, vous définissez une ressource en déclarant une classe. La classe se compose de propriétés qui correspondent aux propriétés de l’objet. Par exemple, dans l’exemple suivant, la classe [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est représentée par le MOF suivant.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

Chaque nom de propriété est précédé d’un type de données. Les types de données de cet exemple correspondent aux types de données CLR primitifs dans le .NET Framework, mais les propriétés peuvent également être des références à d’autres ressources ou types complexes, qui sont tous deux décrits ultérieurement.

Le qualificateur `Key` indique qu’une propriété est utilisée pour identifier de manière unique une instance de ressource. Une ressource peut avoir plusieurs clés.

Le qualificateur `Required` indique que la propriété est obligatoire. Si une propriété est étiquetée avec le qualificateur `Key`, elle est considérée comme étant obligatoire et le qualificateur `Required` n’est pas nécessaire.

### <a name="complex-data-types"></a>Types de données complexes

Les propriétés des entités peuvent avoir des types de données complexes. Les types de données complexes sont des types qui sont constitués d’autres types, comme des structs dans le langage de programmation C. Un type complexe est déclaré dans le fichier MOF en tant que classe avec le qualificateur `ComplexType`, comme dans l’exemple suivant.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Pour déclarer une propriété d’entité en tant que type complexe, vous devez la déclarer en tant que type de `string` avec le qualificateur `EmbeddedInstance`, y compris le nom du type complexe. L’exemple suivant illustre la déclaration d’une propriété du type `PswsTest_ProcessModule` déclaré dans l’exemple précédent.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associer des entités

Vous pouvez associer deux entités à l’aide des qualificateurs Association et AssociationClass. Pour plus d’informations, consultez [Association d’entités de gestion OData](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Types dérivés

Vous pouvez dériver un type à partir d’un autre type. Le type dérivé hérite de toutes les propriétés du type à partir duquel il dérive, en plus des propriétés dérivées explicitement. L’exemple suivant illustre une déclaration de type, puis une déclaration de deux types dérivés de ce type.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```