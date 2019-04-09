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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117433"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="574cf-102">ICLRPolicyManager::SetActionOnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="574cf-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="574cf-103">Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy wystąpi awaria określonej.</span><span class="sxs-lookup"><span data-stu-id="574cf-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="574cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="574cf-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="574cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="574cf-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="574cf-106">[in] Jedną z [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości, wskazujący typ awarii, do których chcesz podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="574cf-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="574cf-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję do wykonania, kiedy wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="574cf-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="574cf-108">Aby uzyskać listę obsługiwanych wartości zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="574cf-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="574cf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="574cf-109">Return Value</span></span>  
  
|<span data-ttu-id="574cf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="574cf-110">HRESULT</span></span>|<span data-ttu-id="574cf-111">Opis</span><span class="sxs-lookup"><span data-stu-id="574cf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="574cf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="574cf-112">S_OK</span></span>|`SetActionOnFailure` <span data-ttu-id="574cf-113">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="574cf-113">returned successfully.</span></span>|  
|<span data-ttu-id="574cf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="574cf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="574cf-115">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="574cf-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="574cf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="574cf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="574cf-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="574cf-117">The call timed out.</span></span>|  
|<span data-ttu-id="574cf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="574cf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="574cf-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="574cf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="574cf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="574cf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="574cf-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="574cf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="574cf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="574cf-122">E_FAIL</span></span>|<span data-ttu-id="574cf-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="574cf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="574cf-124">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="574cf-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="574cf-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="574cf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="574cf-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="574cf-126">E_INVALIDARG</span></span>|<span data-ttu-id="574cf-127">Działanie zasad nie można ustawić dla określonej operacji lub nieprawidłowe zasady akcji została określona dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="574cf-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="574cf-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="574cf-128">Remarks</span></span>  
 <span data-ttu-id="574cf-129">Domyślnie środowisko CLR zgłasza wyjątek, gdy go nie powiedzie się do przydzielenia zasobu, takie jak pamięć.</span><span class="sxs-lookup"><span data-stu-id="574cf-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> `SetActionOnFailure` <span data-ttu-id="574cf-130">Zezwalaj hostowi na zastąpienie tego zachowania, określając zasady działanie podejmowane w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="574cf-130">allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="574cf-131">W poniższej tabeli przedstawiono kombinacje [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) i [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="574cf-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="574cf-132">(Prefiks FAIL_ pominięto w [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości.)</span><span class="sxs-lookup"><span data-stu-id="574cf-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="574cf-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="574cf-133">NonCriticalResource</span></span>|<span data-ttu-id="574cf-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="574cf-134">CriticalResource</span></span>|<span data-ttu-id="574cf-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="574cf-135">FatalRuntime</span></span>|<span data-ttu-id="574cf-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="574cf-136">OrphanedLock</span></span>|<span data-ttu-id="574cf-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="574cf-137">StackOverflow</span></span>|<span data-ttu-id="574cf-138">Naruszenie zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="574cf-138">AccessViolation</span></span>|<span data-ttu-id="574cf-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="574cf-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="574cf-140">X</span><span class="sxs-lookup"><span data-stu-id="574cf-140">X</span></span>|<span data-ttu-id="574cf-141">X</span><span class="sxs-lookup"><span data-stu-id="574cf-141">X</span></span>||||<span data-ttu-id="574cf-142">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-142">N/A</span></span>||  
|<span data-ttu-id="574cf-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="574cf-143">eThrowException</span></span>|<span data-ttu-id="574cf-144">X</span><span class="sxs-lookup"><span data-stu-id="574cf-144">X</span></span>|<span data-ttu-id="574cf-145">X</span><span class="sxs-lookup"><span data-stu-id="574cf-145">X</span></span>||||<span data-ttu-id="574cf-146">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="574cf-147">X</span><span class="sxs-lookup"><span data-stu-id="574cf-147">X</span></span>|<span data-ttu-id="574cf-148">X</span><span class="sxs-lookup"><span data-stu-id="574cf-148">X</span></span>||||<span data-ttu-id="574cf-149">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-149">N/A</span></span>|<span data-ttu-id="574cf-150">X</span><span class="sxs-lookup"><span data-stu-id="574cf-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="574cf-151">X</span><span class="sxs-lookup"><span data-stu-id="574cf-151">X</span></span>|<span data-ttu-id="574cf-152">X</span><span class="sxs-lookup"><span data-stu-id="574cf-152">X</span></span>||||<span data-ttu-id="574cf-153">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-153">N/A</span></span>|<span data-ttu-id="574cf-154">X</span><span class="sxs-lookup"><span data-stu-id="574cf-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="574cf-155">X</span><span class="sxs-lookup"><span data-stu-id="574cf-155">X</span></span>|<span data-ttu-id="574cf-156">X</span><span class="sxs-lookup"><span data-stu-id="574cf-156">X</span></span>||<span data-ttu-id="574cf-157">X</span><span class="sxs-lookup"><span data-stu-id="574cf-157">X</span></span>||<span data-ttu-id="574cf-158">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-158">N/A</span></span>|<span data-ttu-id="574cf-159">X</span><span class="sxs-lookup"><span data-stu-id="574cf-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="574cf-160">X</span><span class="sxs-lookup"><span data-stu-id="574cf-160">X</span></span>|<span data-ttu-id="574cf-161">X</span><span class="sxs-lookup"><span data-stu-id="574cf-161">X</span></span>||<span data-ttu-id="574cf-162">X</span><span class="sxs-lookup"><span data-stu-id="574cf-162">X</span></span>|<span data-ttu-id="574cf-163">X</span><span class="sxs-lookup"><span data-stu-id="574cf-163">X</span></span>|<span data-ttu-id="574cf-164">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-164">N/A</span></span>|<span data-ttu-id="574cf-165">X</span><span class="sxs-lookup"><span data-stu-id="574cf-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="574cf-166">X</span><span class="sxs-lookup"><span data-stu-id="574cf-166">X</span></span>|<span data-ttu-id="574cf-167">X</span><span class="sxs-lookup"><span data-stu-id="574cf-167">X</span></span>||<span data-ttu-id="574cf-168">X</span><span class="sxs-lookup"><span data-stu-id="574cf-168">X</span></span>|<span data-ttu-id="574cf-169">X</span><span class="sxs-lookup"><span data-stu-id="574cf-169">X</span></span>|<span data-ttu-id="574cf-170">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-170">N/A</span></span>|<span data-ttu-id="574cf-171">X</span><span class="sxs-lookup"><span data-stu-id="574cf-171">X</span></span>|  
|<span data-ttu-id="574cf-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="574cf-172">eFastExitProcess</span></span>|<span data-ttu-id="574cf-173">X</span><span class="sxs-lookup"><span data-stu-id="574cf-173">X</span></span>|<span data-ttu-id="574cf-174">X</span><span class="sxs-lookup"><span data-stu-id="574cf-174">X</span></span>||<span data-ttu-id="574cf-175">X</span><span class="sxs-lookup"><span data-stu-id="574cf-175">X</span></span>|<span data-ttu-id="574cf-176">X</span><span class="sxs-lookup"><span data-stu-id="574cf-176">X</span></span>|<span data-ttu-id="574cf-177">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="574cf-178">X</span><span class="sxs-lookup"><span data-stu-id="574cf-178">X</span></span>|<span data-ttu-id="574cf-179">X</span><span class="sxs-lookup"><span data-stu-id="574cf-179">X</span></span>|<span data-ttu-id="574cf-180">X</span><span class="sxs-lookup"><span data-stu-id="574cf-180">X</span></span>|<span data-ttu-id="574cf-181">X</span><span class="sxs-lookup"><span data-stu-id="574cf-181">X</span></span>|<span data-ttu-id="574cf-182">X</span><span class="sxs-lookup"><span data-stu-id="574cf-182">X</span></span>|<span data-ttu-id="574cf-183">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="574cf-184">X</span><span class="sxs-lookup"><span data-stu-id="574cf-184">X</span></span>|<span data-ttu-id="574cf-185">X</span><span class="sxs-lookup"><span data-stu-id="574cf-185">X</span></span>|<span data-ttu-id="574cf-186">X</span><span class="sxs-lookup"><span data-stu-id="574cf-186">X</span></span>|<span data-ttu-id="574cf-187">X</span><span class="sxs-lookup"><span data-stu-id="574cf-187">X</span></span>|<span data-ttu-id="574cf-188">X</span><span class="sxs-lookup"><span data-stu-id="574cf-188">X</span></span>|<span data-ttu-id="574cf-189">Brak</span><span class="sxs-lookup"><span data-stu-id="574cf-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="574cf-190">Wymagania</span><span class="sxs-lookup"><span data-stu-id="574cf-190">Requirements</span></span>  
 <span data-ttu-id="574cf-191">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="574cf-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="574cf-192">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="574cf-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="574cf-193">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="574cf-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="574cf-194">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="574cf-194">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="574cf-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="574cf-195">See also</span></span>

- [<span data-ttu-id="574cf-196">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="574cf-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="574cf-197">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="574cf-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="574cf-198">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="574cf-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="574cf-199">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="574cf-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
