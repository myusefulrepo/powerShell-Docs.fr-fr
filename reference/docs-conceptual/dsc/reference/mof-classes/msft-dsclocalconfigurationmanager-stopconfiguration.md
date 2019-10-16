---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration, méthode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953356"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="28272-103">StopConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="28272-103">StopConfiguration method</span></span>

<span data-ttu-id="28272-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="28272-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="28272-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28272-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="28272-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28272-106">Parameters</span></span>

<span data-ttu-id="28272-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="28272-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="28272-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="28272-108">Return value</span></span>

<span data-ttu-id="28272-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="28272-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="28272-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="28272-110">Remarks</span></span>

<span data-ttu-id="28272-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="28272-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="28272-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="28272-112">Requirements</span></span>

<span data-ttu-id="28272-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="28272-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="28272-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="28272-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="28272-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28272-115">See also</span></span>

[<span data-ttu-id="28272-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="28272-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)