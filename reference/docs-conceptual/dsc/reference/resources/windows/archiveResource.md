---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource Archive DSC
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954766"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="dcdc3-103">Ressource Archive DSC</span><span class="sxs-lookup"><span data-stu-id="dcdc3-103">DSC Archive Resource</span></span>

> <span data-ttu-id="dcdc3-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="dcdc3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="dcdc3-105">La ressource Archive de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcdc3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdc3-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dcdc3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="dcdc3-107">Properties</span></span>

|<span data-ttu-id="dcdc3-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="dcdc3-108">Property</span></span> |<span data-ttu-id="dcdc3-109">Description</span><span class="sxs-lookup"><span data-stu-id="dcdc3-109">Description</span></span> |
|---|---|
|<span data-ttu-id="dcdc3-110">Destination</span><span class="sxs-lookup"><span data-stu-id="dcdc3-110">Destination</span></span> |<span data-ttu-id="dcdc3-111">Spécifie l’emplacement où le contenu de l’archive doit être extrait.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="dcdc3-112">Path</span><span class="sxs-lookup"><span data-stu-id="dcdc3-112">Path</span></span> |<span data-ttu-id="dcdc3-113">Spécifie le chemin source du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="dcdc3-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="dcdc3-114">Checksum</span></span> |<span data-ttu-id="dcdc3-115">Définit le type à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="dcdc3-116">Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="dcdc3-117">Les valeurs valides sont les suivantes : **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="dcdc3-118">Si vous spécifiez **Checksum** sans **Validate**, la configuration échoue.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="dcdc3-119">Force</span><span class="sxs-lookup"><span data-stu-id="dcdc3-119">Force</span></span> |<span data-ttu-id="dcdc3-120">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="dcdc3-121">La propriété **Force** permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="dcdc3-122">La valeur par défaut est **False**.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-122">The default value is **False**.</span></span> |
|<span data-ttu-id="dcdc3-123">Validate</span><span class="sxs-lookup"><span data-stu-id="dcdc3-123">Validate</span></span>| <span data-ttu-id="dcdc3-124">Utilise la propriété **Checksum** pour déterminer si l’archive correspond à la signature.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="dcdc3-125">Si vous spécifiez **Checksum** sans **Validate**, la configuration échoue.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="dcdc3-126">Si vous spécifiez **Validate** sans **Checksum**, la valeur _SHA-256_ est utilisée par défaut pour **Checksum**.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dcdc3-127">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="dcdc3-127">Common properties</span></span>

|<span data-ttu-id="dcdc3-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="dcdc3-128">Property</span></span> |<span data-ttu-id="dcdc3-129">Description</span><span class="sxs-lookup"><span data-stu-id="dcdc3-129">Description</span></span> |
|---|---|
|<span data-ttu-id="dcdc3-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dcdc3-130">DependsOn</span></span> |<span data-ttu-id="dcdc3-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dcdc3-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dcdc3-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="dcdc3-133">Ensure</span></span> |<span data-ttu-id="dcdc3-134">Détermine s’il faut vérifier que le contenu de l’archive se trouve à la **Destination** donnée.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="dcdc3-135">Définissez cette propriété sur **Present** pour vous assurer que le contenu se trouve à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="dcdc3-136">Définissez la propriété sur **Absent** pour vous assurer que le contenu ne se trouve pas à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="dcdc3-137">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="dcdc3-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dcdc3-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="dcdc3-139">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dcdc3-140">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dcdc3-141">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="dcdc3-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="dcdc3-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcdc3-142">Example</span></span>

<span data-ttu-id="dcdc3-143">L’exemple suivant montre comment utiliser la ressource Archive pour vérifier que le contenu d’un fichier d’archive appelé `Test.zip` existe et qu’il est extrait à une destination donnée.</span><span class="sxs-lookup"><span data-stu-id="dcdc3-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```