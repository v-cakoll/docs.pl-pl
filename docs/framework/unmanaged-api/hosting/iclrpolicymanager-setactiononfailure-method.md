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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504111"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="864f5-102">ICLRPolicyManager::SetActionOnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="864f5-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="864f5-103">Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="864f5-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="864f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="864f5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="864f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="864f5-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="864f5-106">podczas Jedna z wartości [EClrFailure —](eclrfailure-enumeration.md) , wskazująca typ błędu, dla którego należy podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="864f5-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="864f5-107">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję do wykonania w przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="864f5-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="864f5-108">Aby zapoznać się z listą obsługiwanych wartości, zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="864f5-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="864f5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="864f5-109">Return Value</span></span>  
  
|<span data-ttu-id="864f5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="864f5-110">HRESULT</span></span>|<span data-ttu-id="864f5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="864f5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="864f5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="864f5-112">S_OK</span></span>|<span data-ttu-id="864f5-113">`SetActionOnFailure`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="864f5-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="864f5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="864f5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="864f5-115">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="864f5-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="864f5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="864f5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="864f5-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="864f5-117">The call timed out.</span></span>|  
|<span data-ttu-id="864f5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="864f5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="864f5-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="864f5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="864f5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="864f5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="864f5-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="864f5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="864f5-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="864f5-122">E_FAIL</span></span>|<span data-ttu-id="864f5-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="864f5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="864f5-124">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="864f5-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="864f5-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="864f5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="864f5-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="864f5-126">E_INVALIDARG</span></span>|<span data-ttu-id="864f5-127">Nie można ustawić akcji zasad dla określonej operacji lub określono nieprawidłową akcję zasad dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="864f5-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="864f5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="864f5-128">Remarks</span></span>  
 <span data-ttu-id="864f5-129">Domyślnie środowisko CLR zgłasza wyjątek, gdy nie może przydzielić zasobu, takiego jak pamięć.</span><span class="sxs-lookup"><span data-stu-id="864f5-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="864f5-130">`SetActionOnFailure`umożliwia hostowi przesłonięcie tego zachowania przez określenie akcji zasad, która ma zostać podjęta po awarii.</span><span class="sxs-lookup"><span data-stu-id="864f5-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="864f5-131">W poniższej tabeli przedstawiono kombinacje obsługiwanych wartości [EClrFailure —](eclrfailure-enumeration.md) i [EPolicyAction —](epolicyaction-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="864f5-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="864f5-132">(Prefiks FAIL_ został pominięty z wartości [EClrFailure —](eclrfailure-enumeration.md) ).</span><span class="sxs-lookup"><span data-stu-id="864f5-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="864f5-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="864f5-133">NonCriticalResource</span></span>|<span data-ttu-id="864f5-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="864f5-134">CriticalResource</span></span>|<span data-ttu-id="864f5-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="864f5-135">FatalRuntime</span></span>|<span data-ttu-id="864f5-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="864f5-136">OrphanedLock</span></span>|<span data-ttu-id="864f5-137">Witryna StackOverflow</span><span class="sxs-lookup"><span data-stu-id="864f5-137">StackOverflow</span></span>|<span data-ttu-id="864f5-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="864f5-138">AccessViolation</span></span>|<span data-ttu-id="864f5-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="864f5-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="864f5-140">X</span><span class="sxs-lookup"><span data-stu-id="864f5-140">X</span></span>|<span data-ttu-id="864f5-141">X</span><span class="sxs-lookup"><span data-stu-id="864f5-141">X</span></span>||||<span data-ttu-id="864f5-142">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-142">N/A</span></span>||  
|<span data-ttu-id="864f5-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="864f5-143">eThrowException</span></span>|<span data-ttu-id="864f5-144">X</span><span class="sxs-lookup"><span data-stu-id="864f5-144">X</span></span>|<span data-ttu-id="864f5-145">X</span><span class="sxs-lookup"><span data-stu-id="864f5-145">X</span></span>||||<span data-ttu-id="864f5-146">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="864f5-147">X</span><span class="sxs-lookup"><span data-stu-id="864f5-147">X</span></span>|<span data-ttu-id="864f5-148">X</span><span class="sxs-lookup"><span data-stu-id="864f5-148">X</span></span>||||<span data-ttu-id="864f5-149">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-149">N/A</span></span>|<span data-ttu-id="864f5-150">X</span><span class="sxs-lookup"><span data-stu-id="864f5-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="864f5-151">X</span><span class="sxs-lookup"><span data-stu-id="864f5-151">X</span></span>|<span data-ttu-id="864f5-152">X</span><span class="sxs-lookup"><span data-stu-id="864f5-152">X</span></span>||||<span data-ttu-id="864f5-153">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-153">N/A</span></span>|<span data-ttu-id="864f5-154">X</span><span class="sxs-lookup"><span data-stu-id="864f5-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="864f5-155">X</span><span class="sxs-lookup"><span data-stu-id="864f5-155">X</span></span>|<span data-ttu-id="864f5-156">X</span><span class="sxs-lookup"><span data-stu-id="864f5-156">X</span></span>||<span data-ttu-id="864f5-157">X</span><span class="sxs-lookup"><span data-stu-id="864f5-157">X</span></span>||<span data-ttu-id="864f5-158">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-158">N/A</span></span>|<span data-ttu-id="864f5-159">X</span><span class="sxs-lookup"><span data-stu-id="864f5-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="864f5-160">X</span><span class="sxs-lookup"><span data-stu-id="864f5-160">X</span></span>|<span data-ttu-id="864f5-161">X</span><span class="sxs-lookup"><span data-stu-id="864f5-161">X</span></span>||<span data-ttu-id="864f5-162">X</span><span class="sxs-lookup"><span data-stu-id="864f5-162">X</span></span>|<span data-ttu-id="864f5-163">X</span><span class="sxs-lookup"><span data-stu-id="864f5-163">X</span></span>|<span data-ttu-id="864f5-164">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-164">N/A</span></span>|<span data-ttu-id="864f5-165">X</span><span class="sxs-lookup"><span data-stu-id="864f5-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="864f5-166">X</span><span class="sxs-lookup"><span data-stu-id="864f5-166">X</span></span>|<span data-ttu-id="864f5-167">X</span><span class="sxs-lookup"><span data-stu-id="864f5-167">X</span></span>||<span data-ttu-id="864f5-168">X</span><span class="sxs-lookup"><span data-stu-id="864f5-168">X</span></span>|<span data-ttu-id="864f5-169">X</span><span class="sxs-lookup"><span data-stu-id="864f5-169">X</span></span>|<span data-ttu-id="864f5-170">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-170">N/A</span></span>|<span data-ttu-id="864f5-171">X</span><span class="sxs-lookup"><span data-stu-id="864f5-171">X</span></span>|  
|<span data-ttu-id="864f5-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="864f5-172">eFastExitProcess</span></span>|<span data-ttu-id="864f5-173">X</span><span class="sxs-lookup"><span data-stu-id="864f5-173">X</span></span>|<span data-ttu-id="864f5-174">X</span><span class="sxs-lookup"><span data-stu-id="864f5-174">X</span></span>||<span data-ttu-id="864f5-175">X</span><span class="sxs-lookup"><span data-stu-id="864f5-175">X</span></span>|<span data-ttu-id="864f5-176">X</span><span class="sxs-lookup"><span data-stu-id="864f5-176">X</span></span>|<span data-ttu-id="864f5-177">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="864f5-178">X</span><span class="sxs-lookup"><span data-stu-id="864f5-178">X</span></span>|<span data-ttu-id="864f5-179">X</span><span class="sxs-lookup"><span data-stu-id="864f5-179">X</span></span>|<span data-ttu-id="864f5-180">X</span><span class="sxs-lookup"><span data-stu-id="864f5-180">X</span></span>|<span data-ttu-id="864f5-181">X</span><span class="sxs-lookup"><span data-stu-id="864f5-181">X</span></span>|<span data-ttu-id="864f5-182">X</span><span class="sxs-lookup"><span data-stu-id="864f5-182">X</span></span>|<span data-ttu-id="864f5-183">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="864f5-184">X</span><span class="sxs-lookup"><span data-stu-id="864f5-184">X</span></span>|<span data-ttu-id="864f5-185">X</span><span class="sxs-lookup"><span data-stu-id="864f5-185">X</span></span>|<span data-ttu-id="864f5-186">X</span><span class="sxs-lookup"><span data-stu-id="864f5-186">X</span></span>|<span data-ttu-id="864f5-187">X</span><span class="sxs-lookup"><span data-stu-id="864f5-187">X</span></span>|<span data-ttu-id="864f5-188">X</span><span class="sxs-lookup"><span data-stu-id="864f5-188">X</span></span>|<span data-ttu-id="864f5-189">Brak</span><span class="sxs-lookup"><span data-stu-id="864f5-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="864f5-190">Wymagania</span><span class="sxs-lookup"><span data-stu-id="864f5-190">Requirements</span></span>  
 <span data-ttu-id="864f5-191">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="864f5-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="864f5-192">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="864f5-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="864f5-193">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="864f5-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="864f5-194">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="864f5-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864f5-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="864f5-195">See also</span></span>

- [<span data-ttu-id="864f5-196">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="864f5-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="864f5-197">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="864f5-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="864f5-198">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="864f5-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="864f5-199">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="864f5-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
