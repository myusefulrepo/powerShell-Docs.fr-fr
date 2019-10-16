---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource DSC PackageManagement
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953236"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="468de-103">Ressource DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="468de-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="468de-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0 et Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="468de-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="468de-105">La ressource **PackageManagement** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="468de-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="468de-106">Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site [http://PowerShellGallery.com](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="468de-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="468de-107">Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.</span><span class="sxs-lookup"><span data-stu-id="468de-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="468de-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="468de-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="468de-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="468de-109">Properties</span></span>

|<span data-ttu-id="468de-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="468de-110">Property</span></span> |<span data-ttu-id="468de-111">Description</span><span class="sxs-lookup"><span data-stu-id="468de-111">Description</span></span> |
|---|---|
|<span data-ttu-id="468de-112">Name</span><span class="sxs-lookup"><span data-stu-id="468de-112">Name</span></span> |<span data-ttu-id="468de-113">Spécifie le nom du package à installer ou à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="468de-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="468de-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="468de-114">AdditionalParameters</span></span> |<span data-ttu-id="468de-115">Table de hachage spécifique du fournisseur, contenant les paramètres passés à `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="468de-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="468de-116">Par exemple, pour le fournisseur NuGet, vous pouvez passer des paramètres supplémentaires tels que DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="468de-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="468de-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="468de-117">MaximumVersion</span></span> |<span data-ttu-id="468de-118">Spécifie la version maximale autorisée du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="468de-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="468de-119">Si vous n’ajoutez pas ce paramètre, la ressource recherche la version disponible la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="468de-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="468de-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="468de-120">MinimumVersion</span></span> |<span data-ttu-id="468de-121">Spécifie la version minimale autorisée du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="468de-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="468de-122">Si vous n’ajoutez pas ce paramètre, la ressource recherche la version la plus élevée du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="468de-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="468de-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="468de-123">ProviderName</span></span> |<span data-ttu-id="468de-124">Spécifie un nom de fournisseur de package auquel vous souhaitez limiter votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="468de-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="468de-125">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="468de-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="468de-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="468de-126">RequiredVersion</span></span> |<span data-ttu-id="468de-127">Spécifie la version exacte du package à installer.</span><span class="sxs-lookup"><span data-stu-id="468de-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="468de-128">Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus récente du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="468de-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="468de-129">Source</span><span class="sxs-lookup"><span data-stu-id="468de-129">Source</span></span> |<span data-ttu-id="468de-130">Spécifie le nom de la source du package où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="468de-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="468de-131">Il peut s’agir d’un URI ou d’une source inscrite avec `Register-PackageSource` ou une ressource DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="468de-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="468de-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="468de-132">SourceCredential</span></span> |<span data-ttu-id="468de-133">Spécifie un compte d’utilisateur disposant des droits nécessaires pour installer un package pour une source ou un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="468de-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="468de-134">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="468de-134">Additional Parameters</span></span>

<span data-ttu-id="468de-135">Le tableau suivant répertorie les options de la propriété AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="468de-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="468de-136">Paramètre</span><span class="sxs-lookup"><span data-stu-id="468de-136">Parameter</span></span> |<span data-ttu-id="468de-137">Description</span><span class="sxs-lookup"><span data-stu-id="468de-137">Description</span></span> |
|---|---|
|<span data-ttu-id="468de-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="468de-138">DestinationPath</span></span> |<span data-ttu-id="468de-139">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="468de-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="468de-140">Spécifie un emplacement de fichier où vous souhaitez installer le package.</span><span class="sxs-lookup"><span data-stu-id="468de-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="468de-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="468de-141">InstallationPolicy</span></span> |<span data-ttu-id="468de-142">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="468de-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="468de-143">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="468de-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="468de-144">Valeurs possibles : **Untrusted** ou **Trusted**.</span><span class="sxs-lookup"><span data-stu-id="468de-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="468de-145">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="468de-145">Common properties</span></span>

|<span data-ttu-id="468de-146">Propriété</span><span class="sxs-lookup"><span data-stu-id="468de-146">Property</span></span> |<span data-ttu-id="468de-147">Description</span><span class="sxs-lookup"><span data-stu-id="468de-147">Description</span></span> |
|---|---|
|<span data-ttu-id="468de-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="468de-148">DependsOn</span></span> |<span data-ttu-id="468de-149">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="468de-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="468de-150">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="468de-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="468de-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="468de-151">Ensure</span></span> |<span data-ttu-id="468de-152">Détermine si le package doit être installé ou désinstallé.</span><span class="sxs-lookup"><span data-stu-id="468de-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="468de-153">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="468de-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="468de-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="468de-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="468de-155">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="468de-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="468de-156">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="468de-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="468de-157">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="468de-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="468de-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="468de-158">Example</span></span>

<span data-ttu-id="468de-159">Cet exemple installe le package NuGet **JQuery** et le module PowerShell **GistProvider** à l’aide de la ressource DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="468de-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="468de-160">Cet exemple vérifie d’abord que les sources de package nécessaires sont disponibles, puis définit l’état attendu des packages **JQuery** et **GistProvider** (NuGet et PowerShell, respectivement).</span><span class="sxs-lookup"><span data-stu-id="468de-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```