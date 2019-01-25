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
ms.openlocfilehash: 98a2978b440e0e72b3b4c1ac3065fbaf5d70e508
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666101"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="3aee5-102">ICLRHostBindingPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3aee5-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="3aee5-103">Udostępnia metody dla hosta ocenić bieżące zasady powiązania i komunikują się zmiany zasad dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3aee5-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3aee5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3aee5-104">Methods</span></span>  
  
|<span data-ttu-id="3aee5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3aee5-105">Method</span></span>|<span data-ttu-id="3aee5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3aee5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3aee5-107">EvaluatePolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="3aee5-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="3aee5-108">Ocenia zasady tworzenia powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="3aee5-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="3aee5-109">ModifyApplicationPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="3aee5-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="3aee5-110">Modyfikuje zasad tworzenia powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="3aee5-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aee5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3aee5-111">Requirements</span></span>  
 <span data-ttu-id="3aee5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aee5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aee5-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3aee5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3aee5-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3aee5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3aee5-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aee5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aee5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3aee5-116">See also</span></span>
- [<span data-ttu-id="3aee5-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3aee5-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3aee5-118">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="3aee5-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="3aee5-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3aee5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
