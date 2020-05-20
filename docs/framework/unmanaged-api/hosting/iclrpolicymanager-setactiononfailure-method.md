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
ms.openlocfilehash: fb2ecc80f272a3fc9b63b20c5956e7a28f117784
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703461"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="ecb20-102">ICLRPolicyManager::SetActionOnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecb20-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="ecb20-103">Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="ecb20-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecb20-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecb20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecb20-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="ecb20-106">podczas Jedna z wartości [EClrFailure —](eclrfailure-enumeration.md) , wskazująca typ błędu, dla którego należy podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="ecb20-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="ecb20-107">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję do wykonania w przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="ecb20-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="ecb20-108">Aby zapoznać się z listą obsługiwanych wartości, zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="ecb20-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecb20-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ecb20-109">Return Value</span></span>  
  
|<span data-ttu-id="ecb20-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecb20-110">HRESULT</span></span>|<span data-ttu-id="ecb20-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb20-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecb20-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecb20-112">S_OK</span></span>|<span data-ttu-id="ecb20-113">`SetActionOnFailure`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ecb20-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="ecb20-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecb20-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecb20-115">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ecb20-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecb20-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecb20-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecb20-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ecb20-117">The call timed out.</span></span>|  
|<span data-ttu-id="ecb20-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecb20-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecb20-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ecb20-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecb20-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecb20-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecb20-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ecb20-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecb20-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecb20-122">E_FAIL</span></span>|<span data-ttu-id="ecb20-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ecb20-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecb20-124">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="ecb20-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecb20-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecb20-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecb20-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ecb20-126">E_INVALIDARG</span></span>|<span data-ttu-id="ecb20-127">Nie można ustawić akcji zasad dla określonej operacji lub określono nieprawidłową akcję zasad dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="ecb20-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb20-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecb20-128">Remarks</span></span>  
 <span data-ttu-id="ecb20-129">Domyślnie środowisko CLR zgłasza wyjątek, gdy nie może przydzielić zasobu, takiego jak pamięć.</span><span class="sxs-lookup"><span data-stu-id="ecb20-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="ecb20-130">`SetActionOnFailure`umożliwia hostowi przesłonięcie tego zachowania przez określenie akcji zasad, która ma zostać podjęta po awarii.</span><span class="sxs-lookup"><span data-stu-id="ecb20-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="ecb20-131">W poniższej tabeli przedstawiono kombinacje obsługiwanych wartości [EClrFailure —](eclrfailure-enumeration.md) i [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ecb20-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="ecb20-132">(Prefiks FAIL_ został pominięty z wartości [EClrFailure —](eclrfailure-enumeration.md) ).</span><span class="sxs-lookup"><span data-stu-id="ecb20-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="ecb20-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="ecb20-133">NonCriticalResource</span></span>|<span data-ttu-id="ecb20-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="ecb20-134">CriticalResource</span></span>|<span data-ttu-id="ecb20-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="ecb20-135">FatalRuntime</span></span>|<span data-ttu-id="ecb20-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="ecb20-136">OrphanedLock</span></span>|<span data-ttu-id="ecb20-137">Witryna StackOverflow</span><span class="sxs-lookup"><span data-stu-id="ecb20-137">StackOverflow</span></span>|<span data-ttu-id="ecb20-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="ecb20-138">AccessViolation</span></span>|<span data-ttu-id="ecb20-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="ecb20-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="ecb20-140">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-140">X</span></span>|<span data-ttu-id="ecb20-141">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-141">X</span></span>||||<span data-ttu-id="ecb20-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-142">N/A</span></span>||  
|<span data-ttu-id="ecb20-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="ecb20-143">eThrowException</span></span>|<span data-ttu-id="ecb20-144">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-144">X</span></span>|<span data-ttu-id="ecb20-145">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-145">X</span></span>||||<span data-ttu-id="ecb20-146">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="ecb20-147">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-147">X</span></span>|<span data-ttu-id="ecb20-148">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-148">X</span></span>||||<span data-ttu-id="ecb20-149">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-149">N/A</span></span>|<span data-ttu-id="ecb20-150">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="ecb20-151">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-151">X</span></span>|<span data-ttu-id="ecb20-152">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-152">X</span></span>||||<span data-ttu-id="ecb20-153">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-153">N/A</span></span>|<span data-ttu-id="ecb20-154">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="ecb20-155">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-155">X</span></span>|<span data-ttu-id="ecb20-156">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-156">X</span></span>||<span data-ttu-id="ecb20-157">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-157">X</span></span>||<span data-ttu-id="ecb20-158">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-158">N/A</span></span>|<span data-ttu-id="ecb20-159">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="ecb20-160">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-160">X</span></span>|<span data-ttu-id="ecb20-161">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-161">X</span></span>||<span data-ttu-id="ecb20-162">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-162">X</span></span>|<span data-ttu-id="ecb20-163">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-163">X</span></span>|<span data-ttu-id="ecb20-164">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-164">N/A</span></span>|<span data-ttu-id="ecb20-165">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="ecb20-166">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-166">X</span></span>|<span data-ttu-id="ecb20-167">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-167">X</span></span>||<span data-ttu-id="ecb20-168">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-168">X</span></span>|<span data-ttu-id="ecb20-169">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-169">X</span></span>|<span data-ttu-id="ecb20-170">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-170">N/A</span></span>|<span data-ttu-id="ecb20-171">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-171">X</span></span>|  
|<span data-ttu-id="ecb20-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="ecb20-172">eFastExitProcess</span></span>|<span data-ttu-id="ecb20-173">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-173">X</span></span>|<span data-ttu-id="ecb20-174">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-174">X</span></span>||<span data-ttu-id="ecb20-175">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-175">X</span></span>|<span data-ttu-id="ecb20-176">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-176">X</span></span>|<span data-ttu-id="ecb20-177">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="ecb20-178">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-178">X</span></span>|<span data-ttu-id="ecb20-179">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-179">X</span></span>|<span data-ttu-id="ecb20-180">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-180">X</span></span>|<span data-ttu-id="ecb20-181">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-181">X</span></span>|<span data-ttu-id="ecb20-182">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-182">X</span></span>|<span data-ttu-id="ecb20-183">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="ecb20-184">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-184">X</span></span>|<span data-ttu-id="ecb20-185">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-185">X</span></span>|<span data-ttu-id="ecb20-186">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-186">X</span></span>|<span data-ttu-id="ecb20-187">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-187">X</span></span>|<span data-ttu-id="ecb20-188">X</span><span class="sxs-lookup"><span data-stu-id="ecb20-188">X</span></span>|<span data-ttu-id="ecb20-189">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ecb20-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="ecb20-190">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecb20-190">Requirements</span></span>  
 <span data-ttu-id="ecb20-191">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecb20-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb20-192">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecb20-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecb20-193">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecb20-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecb20-194">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecb20-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb20-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecb20-195">See also</span></span>

- [<span data-ttu-id="ecb20-196">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ecb20-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="ecb20-197">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ecb20-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ecb20-198">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ecb20-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ecb20-199">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ecb20-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
