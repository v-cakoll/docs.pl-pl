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
ms.openlocfilehash: 9ed317a451e6e35aeac3bc1b83f78d1400ea5c07
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136443"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="87d87-102">ICLRHostBindingPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="87d87-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="87d87-103">Dostarcza metody dla hosta do szacowania bieżących zasad powiązań i przekazywania zmian zasad dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="87d87-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87d87-104">Metody</span><span class="sxs-lookup"><span data-stu-id="87d87-104">Methods</span></span>  
  
|<span data-ttu-id="87d87-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="87d87-105">Method</span></span>|<span data-ttu-id="87d87-106">Opis</span><span class="sxs-lookup"><span data-stu-id="87d87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87d87-107">EvaluatePolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="87d87-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="87d87-108">Oblicza zasady powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="87d87-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="87d87-109">ModifyApplicationPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="87d87-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="87d87-110">Modyfikuje zasady powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="87d87-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87d87-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87d87-111">Requirements</span></span>  
 <span data-ttu-id="87d87-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d87-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d87-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87d87-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87d87-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87d87-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87d87-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d87-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d87-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87d87-116">See also</span></span>

- [<span data-ttu-id="87d87-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87d87-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="87d87-118">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="87d87-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="87d87-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="87d87-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
