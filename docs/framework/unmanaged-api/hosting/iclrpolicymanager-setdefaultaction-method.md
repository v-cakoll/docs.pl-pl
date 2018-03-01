---
title: "ICLRPolicyManager::SetDefaultAction — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 751853aaf4322c15b44bb9b912d293a081c24ba8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="c8b2e-102">ICLRPolicyManager::SetDefaultAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="c8b2e-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="c8b2e-103">Określa akcję zasad, które środowisko uruchomieniowe języka wspólnego (CLR) należy wykonać po wystąpieniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8b2e-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8b2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8b2e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="c8b2e-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący akcję dla CLR, które można dostosować zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="c8b2e-107">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję zasad CLR powinien wykonać, gdy `operation` występuje.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8b2e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c8b2e-108">Return Value</span></span>  
  
|<span data-ttu-id="c8b2e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8b2e-109">HRESULT</span></span>|<span data-ttu-id="c8b2e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c8b2e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8b2e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8b2e-111">S_OK</span></span>|<span data-ttu-id="c8b2e-112">`SetDefaultAction`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="c8b2e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8b2e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8b2e-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8b2e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8b2e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8b2e-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-116">The call timed out.</span></span>|  
|<span data-ttu-id="c8b2e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8b2e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8b2e-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8b2e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8b2e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8b2e-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8b2e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8b2e-121">E_FAIL</span></span>|<span data-ttu-id="c8b2e-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8b2e-123">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8b2e-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c8b2e-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c8b2e-125">E_INVALIDARG</span></span>|<span data-ttu-id="c8b2e-126">Nieprawidłowy `action` określono `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8b2e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8b2e-127">Remarks</span></span>  
 <span data-ttu-id="c8b2e-128">Nie wszystkie wartości działania zasad można określić jako zachowanie domyślne operacjach aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="c8b2e-129">`SetDefaultAction`Zazwyczaj można tylko przekazać zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="c8b2e-130">Na przykład host można określić, że wątek przerwań przekształcone niegrzeczny wątku przerwań, ale nie można określić odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="c8b2e-131">W poniższej tabeli opisano poprawne `action` wartości dla każdego możliwe `operation` wartość.</span><span class="sxs-lookup"><span data-stu-id="c8b2e-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="c8b2e-132">Wartość`operation`</span><span class="sxs-lookup"><span data-stu-id="c8b2e-132">Value for `operation`</span></span>|<span data-ttu-id="c8b2e-133">Prawidłowe wartości`action`</span><span class="sxs-lookup"><span data-stu-id="c8b2e-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="c8b2e-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="c8b2e-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="c8b2e-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="c8b2e-135">-   eAbortThread</span></span><br /><span data-ttu-id="c8b2e-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="c8b2e-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="c8b2e-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-139">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c8b2e-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c8b2e-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="c8b2e-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c8b2e-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="c8b2e-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="c8b2e-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="c8b2e-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-148">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c8b2e-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c8b2e-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="c8b2e-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-155">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c8b2e-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="c8b2e-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="c8b2e-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-161">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c8b2e-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c8b2e-165">OPR_ProcessExit</span></span>|<span data-ttu-id="c8b2e-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-166">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c8b2e-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="c8b2e-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="c8b2e-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="c8b2e-171">-   eNoAction</span></span><br /><span data-ttu-id="c8b2e-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="c8b2e-172">-   eAbortThread</span></span><br /><span data-ttu-id="c8b2e-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="c8b2e-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="c8b2e-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c8b2e-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c8b2e-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-176">-   eExitProcess</span></span><br /><span data-ttu-id="c8b2e-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="c8b2e-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c8b2e-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c8b2e-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c8b2e-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8b2e-180">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8b2e-180">Requirements</span></span>  
 <span data-ttu-id="c8b2e-181">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2e-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b2e-182">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8b2e-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8b2e-183">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8b2e-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8b2e-184">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b2e-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b2e-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8b2e-185">See Also</span></span>  
 [<span data-ttu-id="c8b2e-186">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8b2e-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="c8b2e-187">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8b2e-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="c8b2e-188">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c8b2e-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
