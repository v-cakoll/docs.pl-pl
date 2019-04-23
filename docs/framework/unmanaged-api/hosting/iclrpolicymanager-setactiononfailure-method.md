---
title: ICLRPolicyManager::SetActionOnFailure — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117433"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="baf27-102">ICLRPolicyManager::SetActionOnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="baf27-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="baf27-103">Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy wystąpi awaria określonej.</span><span class="sxs-lookup"><span data-stu-id="baf27-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf27-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baf27-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baf27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="baf27-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="baf27-106">[in] Jedną z [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości, wskazujący typ awarii, do których chcesz podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="baf27-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="baf27-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję do wykonania, kiedy wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="baf27-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="baf27-108">Aby uzyskać listę obsługiwanych wartości zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="baf27-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baf27-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baf27-109">Return Value</span></span>  
  
|<span data-ttu-id="baf27-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baf27-110">HRESULT</span></span>|<span data-ttu-id="baf27-111">Opis</span><span class="sxs-lookup"><span data-stu-id="baf27-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baf27-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="baf27-112">S_OK</span></span>|<span data-ttu-id="baf27-113">`SetActionOnFailure` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="baf27-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="baf27-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="baf27-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="baf27-115">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="baf27-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="baf27-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="baf27-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="baf27-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="baf27-117">The call timed out.</span></span>|  
|<span data-ttu-id="baf27-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="baf27-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="baf27-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="baf27-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="baf27-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="baf27-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="baf27-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="baf27-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="baf27-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baf27-122">E_FAIL</span></span>|<span data-ttu-id="baf27-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="baf27-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="baf27-124">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="baf27-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="baf27-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="baf27-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="baf27-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="baf27-126">E_INVALIDARG</span></span>|<span data-ttu-id="baf27-127">Działanie zasad nie można ustawić dla określonej operacji lub nieprawidłowe zasady akcji została określona dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="baf27-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf27-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baf27-128">Remarks</span></span>  
 <span data-ttu-id="baf27-129">Domyślnie środowisko CLR zgłasza wyjątek, gdy go nie powiedzie się do przydzielenia zasobu, takie jak pamięć.</span><span class="sxs-lookup"><span data-stu-id="baf27-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="baf27-130">`SetActionOnFailure` Zezwalaj hostowi na zastąpienie tego zachowania, określając zasady działanie podejmowane w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="baf27-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="baf27-131">W poniższej tabeli przedstawiono kombinacje [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) i [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="baf27-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="baf27-132">(Prefiks FAIL_ pominięto w [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości.)</span><span class="sxs-lookup"><span data-stu-id="baf27-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="baf27-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="baf27-133">NonCriticalResource</span></span>|<span data-ttu-id="baf27-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="baf27-134">CriticalResource</span></span>|<span data-ttu-id="baf27-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="baf27-135">FatalRuntime</span></span>|<span data-ttu-id="baf27-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="baf27-136">OrphanedLock</span></span>|<span data-ttu-id="baf27-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="baf27-137">StackOverflow</span></span>|<span data-ttu-id="baf27-138">Naruszenie zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="baf27-138">AccessViolation</span></span>|<span data-ttu-id="baf27-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="baf27-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="baf27-140">X</span><span class="sxs-lookup"><span data-stu-id="baf27-140">X</span></span>|<span data-ttu-id="baf27-141">X</span><span class="sxs-lookup"><span data-stu-id="baf27-141">X</span></span>||||<span data-ttu-id="baf27-142">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-142">N/A</span></span>||  
|<span data-ttu-id="baf27-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="baf27-143">eThrowException</span></span>|<span data-ttu-id="baf27-144">X</span><span class="sxs-lookup"><span data-stu-id="baf27-144">X</span></span>|<span data-ttu-id="baf27-145">X</span><span class="sxs-lookup"><span data-stu-id="baf27-145">X</span></span>||||<span data-ttu-id="baf27-146">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="baf27-147">X</span><span class="sxs-lookup"><span data-stu-id="baf27-147">X</span></span>|<span data-ttu-id="baf27-148">X</span><span class="sxs-lookup"><span data-stu-id="baf27-148">X</span></span>||||<span data-ttu-id="baf27-149">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-149">N/A</span></span>|<span data-ttu-id="baf27-150">X</span><span class="sxs-lookup"><span data-stu-id="baf27-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="baf27-151">X</span><span class="sxs-lookup"><span data-stu-id="baf27-151">X</span></span>|<span data-ttu-id="baf27-152">X</span><span class="sxs-lookup"><span data-stu-id="baf27-152">X</span></span>||||<span data-ttu-id="baf27-153">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-153">N/A</span></span>|<span data-ttu-id="baf27-154">X</span><span class="sxs-lookup"><span data-stu-id="baf27-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="baf27-155">X</span><span class="sxs-lookup"><span data-stu-id="baf27-155">X</span></span>|<span data-ttu-id="baf27-156">X</span><span class="sxs-lookup"><span data-stu-id="baf27-156">X</span></span>||<span data-ttu-id="baf27-157">X</span><span class="sxs-lookup"><span data-stu-id="baf27-157">X</span></span>||<span data-ttu-id="baf27-158">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-158">N/A</span></span>|<span data-ttu-id="baf27-159">X</span><span class="sxs-lookup"><span data-stu-id="baf27-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="baf27-160">X</span><span class="sxs-lookup"><span data-stu-id="baf27-160">X</span></span>|<span data-ttu-id="baf27-161">X</span><span class="sxs-lookup"><span data-stu-id="baf27-161">X</span></span>||<span data-ttu-id="baf27-162">X</span><span class="sxs-lookup"><span data-stu-id="baf27-162">X</span></span>|<span data-ttu-id="baf27-163">X</span><span class="sxs-lookup"><span data-stu-id="baf27-163">X</span></span>|<span data-ttu-id="baf27-164">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-164">N/A</span></span>|<span data-ttu-id="baf27-165">X</span><span class="sxs-lookup"><span data-stu-id="baf27-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="baf27-166">X</span><span class="sxs-lookup"><span data-stu-id="baf27-166">X</span></span>|<span data-ttu-id="baf27-167">X</span><span class="sxs-lookup"><span data-stu-id="baf27-167">X</span></span>||<span data-ttu-id="baf27-168">X</span><span class="sxs-lookup"><span data-stu-id="baf27-168">X</span></span>|<span data-ttu-id="baf27-169">X</span><span class="sxs-lookup"><span data-stu-id="baf27-169">X</span></span>|<span data-ttu-id="baf27-170">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-170">N/A</span></span>|<span data-ttu-id="baf27-171">X</span><span class="sxs-lookup"><span data-stu-id="baf27-171">X</span></span>|  
|<span data-ttu-id="baf27-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="baf27-172">eFastExitProcess</span></span>|<span data-ttu-id="baf27-173">X</span><span class="sxs-lookup"><span data-stu-id="baf27-173">X</span></span>|<span data-ttu-id="baf27-174">X</span><span class="sxs-lookup"><span data-stu-id="baf27-174">X</span></span>||<span data-ttu-id="baf27-175">X</span><span class="sxs-lookup"><span data-stu-id="baf27-175">X</span></span>|<span data-ttu-id="baf27-176">X</span><span class="sxs-lookup"><span data-stu-id="baf27-176">X</span></span>|<span data-ttu-id="baf27-177">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="baf27-178">X</span><span class="sxs-lookup"><span data-stu-id="baf27-178">X</span></span>|<span data-ttu-id="baf27-179">X</span><span class="sxs-lookup"><span data-stu-id="baf27-179">X</span></span>|<span data-ttu-id="baf27-180">X</span><span class="sxs-lookup"><span data-stu-id="baf27-180">X</span></span>|<span data-ttu-id="baf27-181">X</span><span class="sxs-lookup"><span data-stu-id="baf27-181">X</span></span>|<span data-ttu-id="baf27-182">X</span><span class="sxs-lookup"><span data-stu-id="baf27-182">X</span></span>|<span data-ttu-id="baf27-183">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="baf27-184">X</span><span class="sxs-lookup"><span data-stu-id="baf27-184">X</span></span>|<span data-ttu-id="baf27-185">X</span><span class="sxs-lookup"><span data-stu-id="baf27-185">X</span></span>|<span data-ttu-id="baf27-186">X</span><span class="sxs-lookup"><span data-stu-id="baf27-186">X</span></span>|<span data-ttu-id="baf27-187">X</span><span class="sxs-lookup"><span data-stu-id="baf27-187">X</span></span>|<span data-ttu-id="baf27-188">X</span><span class="sxs-lookup"><span data-stu-id="baf27-188">X</span></span>|<span data-ttu-id="baf27-189">Brak</span><span class="sxs-lookup"><span data-stu-id="baf27-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="baf27-190">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baf27-190">Requirements</span></span>  
 <span data-ttu-id="baf27-191">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baf27-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baf27-192">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baf27-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baf27-193">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="baf27-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baf27-194">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baf27-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf27-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baf27-195">See also</span></span>

- [<span data-ttu-id="baf27-196">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="baf27-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="baf27-197">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="baf27-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="baf27-198">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="baf27-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="baf27-199">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="baf27-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
