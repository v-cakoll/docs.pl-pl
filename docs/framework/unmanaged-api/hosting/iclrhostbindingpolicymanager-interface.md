---
title: ICLRHostBindingPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e494bbbd08a77329b7b64816216e4bb2e1b724a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074199"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="341e7-102">ICLRHostBindingPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="341e7-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="341e7-103">Udostępnia metody dla hosta ocenić bieżące zasady powiązania i komunikują się zmiany zasad dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="341e7-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="341e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="341e7-104">Methods</span></span>  
  
|<span data-ttu-id="341e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="341e7-105">Method</span></span>|<span data-ttu-id="341e7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="341e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="341e7-107">EvaluatePolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="341e7-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="341e7-108">Ocenia zasady tworzenia powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="341e7-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="341e7-109">ModifyApplicationPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="341e7-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="341e7-110">Modyfikuje zasad tworzenia powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="341e7-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="341e7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="341e7-111">Requirements</span></span>  
 <span data-ttu-id="341e7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="341e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="341e7-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="341e7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="341e7-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="341e7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="341e7-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="341e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341e7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="341e7-116">See also</span></span>

- [<span data-ttu-id="341e7-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="341e7-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="341e7-118">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="341e7-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="341e7-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="341e7-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
