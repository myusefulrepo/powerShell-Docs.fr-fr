---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippet
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736962"
---
# <a name="the-isesnippetobject"></a>Objet ISESnippet

Un objet **ISESnippet** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISESnippet. Les membres de la collection `$psISE.CurrentPowerShellTab.Snippets` sont tous des exemples d’objets **ISESnippet**. La façon la plus simple de créer un extrait de code est d’utiliser la cmdlet [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md).

## <a name="properties"></a>Propriétés

### <a name="author"></a>Auteur

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le nom de l’auteur de l’extrait de code.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le fragment de code à insérer dans l’éditeur.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Raccourci

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le raccourci clavier Windows associé à l’élément de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Voir aussi

- [Objet ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
