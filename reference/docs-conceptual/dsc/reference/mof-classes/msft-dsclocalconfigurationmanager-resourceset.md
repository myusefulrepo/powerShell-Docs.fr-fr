---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceSet, méthode
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954956"
---
# <a name="resourceset-method"></a><span data-ttu-id="f32b5-103">ResourceSet, méthode</span><span class="sxs-lookup"><span data-stu-id="f32b5-103">ResourceSet method</span></span>

<span data-ttu-id="f32b5-104">Appelle directement la méthode **Set** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="f32b5-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="f32b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f32b5-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="f32b5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f32b5-106">Parameters</span></span>

<span data-ttu-id="f32b5-107">*ResourceType* \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="f32b5-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f32b5-108">*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="f32b5-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f32b5-109">*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f32b5-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f32b5-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="f32b5-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f32b5-111">*RebootRequired* \[out\] En retour, cette propriété prend la valeur **true** si le nœud cible doit être redémarré.</span><span class="sxs-lookup"><span data-stu-id="f32b5-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="f32b5-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f32b5-112">Return value</span></span>

<span data-ttu-id="f32b5-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f32b5-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f32b5-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="f32b5-114">Remarks</span></span>

<span data-ttu-id="f32b5-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="f32b5-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f32b5-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f32b5-116">Requirements</span></span>

<span data-ttu-id="f32b5-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f32b5-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f32b5-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f32b5-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f32b5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f32b5-119">See also</span></span>

[<span data-ttu-id="f32b5-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f32b5-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)