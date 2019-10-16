---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
description: Fournit un mécanisme permettant de gérer des groupes locaux sur le nœud cible.
title: Ressources GroupSet dans DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953176"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="0fb28-104">Ressources GroupSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="0fb28-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="0fb28-105">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0fb28-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="0fb28-106">La ressource **GroupSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0fb28-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="0fb28-107">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la ressource [Group resource](groupResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="0fb28-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="0fb28-108">Utilisez cette ressource quand vous souhaitez ajouter ou supprimer la même liste de membres dans plusieurs groupes, supprimer plusieurs groupes, ou ajouter plusieurs groupes avec la même liste de membres.</span><span class="sxs-lookup"><span data-stu-id="0fb28-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fb28-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fb28-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0fb28-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0fb28-110">Properties</span></span>

|<span data-ttu-id="0fb28-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="0fb28-111">Property</span></span> |<span data-ttu-id="0fb28-112">Description</span><span class="sxs-lookup"><span data-stu-id="0fb28-112">Description</span></span> |
|---|---|
|<span data-ttu-id="0fb28-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="0fb28-113">GroupName</span></span> |<span data-ttu-id="0fb28-114">Noms des groupes pour lesquels vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="0fb28-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0fb28-115">Members</span><span class="sxs-lookup"><span data-stu-id="0fb28-115">Members</span></span> |<span data-ttu-id="0fb28-116">Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0fb28-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="0fb28-117">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="0fb28-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0fb28-118">Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="0fb28-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="0fb28-119">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="0fb28-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0fb28-120">Description</span><span class="sxs-lookup"><span data-stu-id="0fb28-120">Description</span></span> |<span data-ttu-id="0fb28-121">La description du groupe.</span><span class="sxs-lookup"><span data-stu-id="0fb28-121">The description of the group.</span></span> |
|<span data-ttu-id="0fb28-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="0fb28-122">MembersToInclude</span></span> |<span data-ttu-id="0fb28-123">Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="0fb28-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="0fb28-124">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="0fb28-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0fb28-125">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="0fb28-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0fb28-126">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="0fb28-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0fb28-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="0fb28-127">MembersToExclude</span></span> |<span data-ttu-id="0fb28-128">Utilisez cette propriété pour supprimer des membres de l’appartenance existante des groupes.</span><span class="sxs-lookup"><span data-stu-id="0fb28-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="0fb28-129">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="0fb28-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0fb28-130">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="0fb28-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0fb28-131">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="0fb28-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0fb28-132">Credential</span><span class="sxs-lookup"><span data-stu-id="0fb28-132">Credential</span></span> |<span data-ttu-id="0fb28-133">Les informations d’identification devant être fournies pour accéder aux ressources distantes.</span><span class="sxs-lookup"><span data-stu-id="0fb28-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="0fb28-134">Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="0fb28-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0fb28-135">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="0fb28-135">Common properties</span></span>

|<span data-ttu-id="0fb28-136">Propriété</span><span class="sxs-lookup"><span data-stu-id="0fb28-136">Property</span></span> |<span data-ttu-id="0fb28-137">Description</span><span class="sxs-lookup"><span data-stu-id="0fb28-137">Description</span></span> |
|---|---|
|<span data-ttu-id="0fb28-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0fb28-138">DependsOn</span></span> |<span data-ttu-id="0fb28-139">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0fb28-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0fb28-140">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0fb28-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0fb28-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="0fb28-141">Ensure</span></span> |<span data-ttu-id="0fb28-142">Indique si les groupes existent.</span><span class="sxs-lookup"><span data-stu-id="0fb28-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="0fb28-143">Définissez cette propriété sur **Absent** pour faire en sorte que les groupes n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="0fb28-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="0fb28-144">La valeur **Present** garantit l’existence du groupe.</span><span class="sxs-lookup"><span data-stu-id="0fb28-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="0fb28-145">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="0fb28-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="0fb28-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0fb28-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="0fb28-147">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="0fb28-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0fb28-148">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="0fb28-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0fb28-149">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="0fb28-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="0fb28-150">Exemple 1 : S’assurer que des groupes sont présents</span><span class="sxs-lookup"><span data-stu-id="0fb28-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="0fb28-151">L’exemple suivant montre comment s’assurer que les deux groupes « myGroup » et « myOtherGroup » sont présents.</span><span class="sxs-lookup"><span data-stu-id="0fb28-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="0fb28-152">Cet exemple utilise des informations d’identification en texte clair par souci de simplicité.</span><span class="sxs-lookup"><span data-stu-id="0fb28-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="0fb28-153">Pour plus d’informations sur la façon de chiffrer des informations d’identification dans le fichier MOF de configuration, consultez [Sécurisation du fichier MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="0fb28-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>