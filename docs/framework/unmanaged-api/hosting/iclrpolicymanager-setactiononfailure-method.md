---
title: "ICLRPolicyManager::SetActionOnFailure — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="c880a-102">ICLRPolicyManager::SetActionOnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="c880a-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="c880a-103">Określa akcję zasady, którą powinno mieć środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi określony błąd.</span><span class="sxs-lookup"><span data-stu-id="c880a-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c880a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c880a-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c880a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c880a-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="c880a-106">[in] Jeden z [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości i wskazujący typ awarii, dla którego podejmowania żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="c880a-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="c880a-107">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję do wykonania, kiedy wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="c880a-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="c880a-108">Listę obsługiwanych wartości znajduje się w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="c880a-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c880a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c880a-109">Return Value</span></span>  
  
|<span data-ttu-id="c880a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c880a-110">HRESULT</span></span>|<span data-ttu-id="c880a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c880a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c880a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c880a-112">S_OK</span></span>|<span data-ttu-id="c880a-113">`SetActionOnFailure`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c880a-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="c880a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c880a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c880a-115">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c880a-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c880a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c880a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c880a-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c880a-117">The call timed out.</span></span>|  
|<span data-ttu-id="c880a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c880a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c880a-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c880a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c880a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c880a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c880a-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c880a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c880a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c880a-122">E_FAIL</span></span>|<span data-ttu-id="c880a-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c880a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c880a-124">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c880a-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c880a-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c880a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c880a-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c880a-126">E_INVALIDARG</span></span>|<span data-ttu-id="c880a-127">Akcja zasad nie można ustawić dla określonej operacji, lub akcji nieprawidłowe zasady został określony dla operacji.</span><span class="sxs-lookup"><span data-stu-id="c880a-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c880a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c880a-128">Remarks</span></span>  
 <span data-ttu-id="c880a-129">Domyślnie środowisko CLR zgłasza wyjątek, kiedy nie powiedzie się przydzielić zasób, takie jak pamięć.</span><span class="sxs-lookup"><span data-stu-id="c880a-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="c880a-130">`SetActionOnFailure`Pozwala zmienić to zachowanie, określając zasady działanie podejmowane w przypadku awarii hosta.</span><span class="sxs-lookup"><span data-stu-id="c880a-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="c880a-131">W poniższej tabeli przedstawiono kombinacje [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) i [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c880a-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="c880a-132">(Został pominięty prefiks FAIL_ [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości.)</span><span class="sxs-lookup"><span data-stu-id="c880a-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="c880a-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="c880a-133">NonCriticalResource</span></span>|<span data-ttu-id="c880a-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="c880a-134">CriticalResource</span></span>|<span data-ttu-id="c880a-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="c880a-135">FatalRuntime</span></span>|<span data-ttu-id="c880a-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="c880a-136">OrphanedLock</span></span>|<span data-ttu-id="c880a-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="c880a-137">StackOverflow</span></span>|<span data-ttu-id="c880a-138">Naruszenie zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="c880a-138">AccessViolation</span></span>|<span data-ttu-id="c880a-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="c880a-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="c880a-140">X</span><span class="sxs-lookup"><span data-stu-id="c880a-140">X</span></span>|<span data-ttu-id="c880a-141">X</span><span class="sxs-lookup"><span data-stu-id="c880a-141">X</span></span>||||<span data-ttu-id="c880a-142">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-142">N/A</span></span>||  
|<span data-ttu-id="c880a-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="c880a-143">eThrowException</span></span>|<span data-ttu-id="c880a-144">X</span><span class="sxs-lookup"><span data-stu-id="c880a-144">X</span></span>|<span data-ttu-id="c880a-145">X</span><span class="sxs-lookup"><span data-stu-id="c880a-145">X</span></span>||||<span data-ttu-id="c880a-146">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="c880a-147">X</span><span class="sxs-lookup"><span data-stu-id="c880a-147">X</span></span>|<span data-ttu-id="c880a-148">X</span><span class="sxs-lookup"><span data-stu-id="c880a-148">X</span></span>||||<span data-ttu-id="c880a-149">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-149">N/A</span></span>|<span data-ttu-id="c880a-150">X</span><span class="sxs-lookup"><span data-stu-id="c880a-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="c880a-151">X</span><span class="sxs-lookup"><span data-stu-id="c880a-151">X</span></span>|<span data-ttu-id="c880a-152">X</span><span class="sxs-lookup"><span data-stu-id="c880a-152">X</span></span>||||<span data-ttu-id="c880a-153">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-153">N/A</span></span>|<span data-ttu-id="c880a-154">X</span><span class="sxs-lookup"><span data-stu-id="c880a-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="c880a-155">X</span><span class="sxs-lookup"><span data-stu-id="c880a-155">X</span></span>|<span data-ttu-id="c880a-156">X</span><span class="sxs-lookup"><span data-stu-id="c880a-156">X</span></span>||<span data-ttu-id="c880a-157">X</span><span class="sxs-lookup"><span data-stu-id="c880a-157">X</span></span>||<span data-ttu-id="c880a-158">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-158">N/A</span></span>|<span data-ttu-id="c880a-159">X</span><span class="sxs-lookup"><span data-stu-id="c880a-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="c880a-160">X</span><span class="sxs-lookup"><span data-stu-id="c880a-160">X</span></span>|<span data-ttu-id="c880a-161">X</span><span class="sxs-lookup"><span data-stu-id="c880a-161">X</span></span>||<span data-ttu-id="c880a-162">X</span><span class="sxs-lookup"><span data-stu-id="c880a-162">X</span></span>|<span data-ttu-id="c880a-163">X</span><span class="sxs-lookup"><span data-stu-id="c880a-163">X</span></span>|<span data-ttu-id="c880a-164">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-164">N/A</span></span>|<span data-ttu-id="c880a-165">X</span><span class="sxs-lookup"><span data-stu-id="c880a-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="c880a-166">X</span><span class="sxs-lookup"><span data-stu-id="c880a-166">X</span></span>|<span data-ttu-id="c880a-167">X</span><span class="sxs-lookup"><span data-stu-id="c880a-167">X</span></span>||<span data-ttu-id="c880a-168">X</span><span class="sxs-lookup"><span data-stu-id="c880a-168">X</span></span>|<span data-ttu-id="c880a-169">X</span><span class="sxs-lookup"><span data-stu-id="c880a-169">X</span></span>|<span data-ttu-id="c880a-170">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-170">N/A</span></span>|<span data-ttu-id="c880a-171">X</span><span class="sxs-lookup"><span data-stu-id="c880a-171">X</span></span>|  
|<span data-ttu-id="c880a-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c880a-172">eFastExitProcess</span></span>|<span data-ttu-id="c880a-173">X</span><span class="sxs-lookup"><span data-stu-id="c880a-173">X</span></span>|<span data-ttu-id="c880a-174">X</span><span class="sxs-lookup"><span data-stu-id="c880a-174">X</span></span>||<span data-ttu-id="c880a-175">X</span><span class="sxs-lookup"><span data-stu-id="c880a-175">X</span></span>|<span data-ttu-id="c880a-176">X</span><span class="sxs-lookup"><span data-stu-id="c880a-176">X</span></span>|<span data-ttu-id="c880a-177">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="c880a-178">X</span><span class="sxs-lookup"><span data-stu-id="c880a-178">X</span></span>|<span data-ttu-id="c880a-179">X</span><span class="sxs-lookup"><span data-stu-id="c880a-179">X</span></span>|<span data-ttu-id="c880a-180">X</span><span class="sxs-lookup"><span data-stu-id="c880a-180">X</span></span>|<span data-ttu-id="c880a-181">X</span><span class="sxs-lookup"><span data-stu-id="c880a-181">X</span></span>|<span data-ttu-id="c880a-182">X</span><span class="sxs-lookup"><span data-stu-id="c880a-182">X</span></span>|<span data-ttu-id="c880a-183">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="c880a-184">X</span><span class="sxs-lookup"><span data-stu-id="c880a-184">X</span></span>|<span data-ttu-id="c880a-185">X</span><span class="sxs-lookup"><span data-stu-id="c880a-185">X</span></span>|<span data-ttu-id="c880a-186">X</span><span class="sxs-lookup"><span data-stu-id="c880a-186">X</span></span>|<span data-ttu-id="c880a-187">X</span><span class="sxs-lookup"><span data-stu-id="c880a-187">X</span></span>|<span data-ttu-id="c880a-188">X</span><span class="sxs-lookup"><span data-stu-id="c880a-188">X</span></span>|<span data-ttu-id="c880a-189">Brak</span><span class="sxs-lookup"><span data-stu-id="c880a-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="c880a-190">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c880a-190">Requirements</span></span>  
 <span data-ttu-id="c880a-191">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c880a-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c880a-192">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c880a-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c880a-193">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c880a-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c880a-194">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c880a-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c880a-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c880a-195">See Also</span></span>  
 [<span data-ttu-id="c880a-196">EClrFailure — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c880a-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="c880a-197">EPolicyAction — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c880a-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="c880a-198">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="c880a-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c880a-199">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c880a-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
