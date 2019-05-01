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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984675"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="2532a-102">ICLRHostBindingPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2532a-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="2532a-103">Udostępnia metody dla hosta ocenić bieżące zasady powiązania i komunikują się zmiany zasad dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2532a-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2532a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2532a-104">Methods</span></span>  
  
|<span data-ttu-id="2532a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2532a-105">Method</span></span>|<span data-ttu-id="2532a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2532a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2532a-107">EvaluatePolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="2532a-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="2532a-108">Ocenia zasady tworzenia powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="2532a-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="2532a-109">ModifyApplicationPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="2532a-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="2532a-110">Modyfikuje zasad tworzenia powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="2532a-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2532a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2532a-111">Requirements</span></span>  
 <span data-ttu-id="2532a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2532a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2532a-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2532a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2532a-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2532a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2532a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2532a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2532a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2532a-116">See also</span></span>

- [<span data-ttu-id="2532a-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2532a-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2532a-118">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="2532a-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="2532a-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2532a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
