---
title: Prise en charge de l’aide en ligne | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360658"
---
# <a name="supporting-online-help"></a>Prise en charge de l’aide en ligne

À compter de Windows PowerShell 3,0, il existe deux façons de prendre en charge la fonctionnalité en ligne `Get-Help` pour les commandes Windows PowerShell. Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commande.

## <a name="about-online-help"></a>À propos de l’aide en ligne

L’aide en ligne a toujours été une partie essentielle de Windows PowerShell. Bien que l’applet de commande `Get-Help` affiche des rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, notamment le codage de couleurs, les liens hypertexte et le partage d’idées dans le contenu de la communauté et les documents basés sur le wiki. Plus important encore, avant l’avènement de l’aide actualisable, l’aide en ligne offrait la version la plus récente des fichiers d’aide.

Avec l’avènement de l’aide actualisable dans Windows PowerShell 3,0, l’aide en ligne joue toujours un rôle vital. En plus de l’expérience utilisateur flexible, l’aide en ligne fournit de l’aide aux utilisateurs qui ne peuvent pas ou ne peuvent pas utiliser l’aide actualisable pour télécharger des rubriques d’aide.

## <a name="how-get-help--online-works"></a>Comment obtenir-Help-Online fonctionne

Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, la commande `Get-Help` possède un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet par défaut de l’utilisateur.

Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l’applet de commande `Invoke-Command`.

```powershell
Get-Help Invoke-Command -Online
```

Pour implémenter `Get-Help` en ligne, l’applet de commande `Get-Help` recherche une Uniform Resource Identifier (URI) pour la rubrique d’aide de la version en ligne aux emplacements suivants.

- Premier lien de la section Liens connexes de la rubrique d’aide de la commande. La rubrique d’aide doit être installée sur l’ordinateur de l’utilisateur. Cette fonctionnalité a été introduite dans Windows PowerShell 2,0.

- Propriété HelpUri de toute commande. La propriété HelpUri est accessible même lorsque la rubrique d’aide de la commande n’est pas installée sur l’ordinateur de l’utilisateur. Cette fonctionnalité a été introduite dans Windows PowerShell 3,0.

  `Get-Help` recherche un URI dans la première entrée de la section Liens connexes avant d’obtenir la valeur de la propriété HelpUri. Si la valeur de la propriété est incorrecte ou a changé, vous pouvez la remplacer en entrant une valeur différente dans le premier lien associé. Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installées sur l’ordinateur de l’utilisateur.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Ajout d’un URI au premier lien associé d’une rubrique d’aide sur une commande

Vous pouvez prendre en charge `Get-Help`-Online pour n’importe quelle commande en ajoutant un URI valide à la première entrée de la section Liens connexes de la rubrique d’aide XML relative à la commande. Cette option est valide uniquement dans les rubriques d’aide XML et fonctionne uniquement lorsque la rubrique d’aide est installée sur l’ordinateur de l’utilisateur. Lorsque la rubrique d’aide est installée et que l’URI est rempli, cette valeur est prioritaire par rapport à la propriété **HelpUri** de la commande.

Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans l’élément `maml:uri` sous le premier élément `maml:relatedLinks/maml:navigationLink` de l’élément `maml:relatedLinks`.

Le code XML suivant montre le positionnement correct de l’URI. Le texte « version en ligne : » dans l’élément `maml:linkText` est une meilleure pratique, mais il n’est pas obligatoire.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Ajout de la propriété HelpUri à une commande

Cette section montre comment ajouter la propriété HelpUri à des commandes de types différents.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Ajout d’une propriété HelpUri à une applet de commande

Pour les applets de C#commande écrites dans, ajoutez un attribut **HelpUri** à la classe cmdlet. La valeur de l’attribut doit être un URI qui commence par « http » ou « HTTPS ».

Le code suivant illustre l’attribut HelpUri de la classe d’applet de commande `Get-History`.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Ajout d’une propriété HelpUri à une fonction avancée

Pour fonctions avancées, ajoutez une propriété **HelpUri** à l’attribut **CmdletBinding** . La valeur de la propriété doit être un URI qui commence par « http » ou « HTTPS ».

Le code suivant illustre l’attribut HelpUri de la fonction New-Calendar

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Ajout d’un attribut HelpUri à une commande CIM

Pour les commandes CIM, ajoutez un attribut **HelpUri** à l’élément **CmdletMetadata** dans le fichier CDXML. La valeur de l’attribut doit être un URI qui commence par « http » ou « HTTPS ».

Le code suivant illustre l’attribut HelpUri de la commande CIM Start-Debug.

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Ajout d’un attribut HelpUri à un Workflow

Pour les flux de travail écrits dans le langage Windows PowerShell, ajoutez un **. Commentaire ExternalHelp** directive de commentaire au code de Workflow. La valeur de la directive doit être un URI qui commence par « http » ou « HTTPS ».

> [!NOTE]
> La propriété HelpUri n’est pas prise en charge pour les flux de travail XAML dans Windows PowerShell.

Le code suivant illustre. Directive commentaire ExternalHelp dans un fichier de flux de travail.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```