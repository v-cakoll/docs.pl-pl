---
title: ICLRPolicyManager::SetActionOnTimeout — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140788"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="cdcf7-102">ICLRPolicyManager::SetActionOnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="cdcf7-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="cdcf7-103">Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR), gdy określona operacja przeprowadzi limit czasu.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcf7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdcf7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdcf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdcf7-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="cdcf7-106">podczas Jedna z wartości [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać określona akcja limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="cdcf7-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="cdcf7-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="cdcf7-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="cdcf7-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="cdcf7-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="cdcf7-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="cdcf7-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="cdcf7-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="cdcf7-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="cdcf7-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="cdcf7-112">podczas Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , wskazująca akcję zasad, która ma zostać podjęta po przełączeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdcf7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdcf7-113">Return Value</span></span>  
  
|<span data-ttu-id="cdcf7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdcf7-114">HRESULT</span></span>|<span data-ttu-id="cdcf7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cdcf7-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdcf7-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="cdcf7-116">S_OK</span></span>|<span data-ttu-id="cdcf7-117">`SetActionOnTimeout` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="cdcf7-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cdcf7-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cdcf7-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cdcf7-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cdcf7-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cdcf7-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-121">The call timed out.</span></span>|  
|<span data-ttu-id="cdcf7-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cdcf7-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cdcf7-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cdcf7-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cdcf7-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cdcf7-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cdcf7-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cdcf7-126">E_FAIL</span></span>|<span data-ttu-id="cdcf7-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cdcf7-128">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cdcf7-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cdcf7-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cdcf7-130">E_INVALIDARG</span></span>|<span data-ttu-id="cdcf7-131">Nie można ustawić limitu czasu dla określonego `operation`lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdcf7-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdcf7-132">Remarks</span></span>  
 <span data-ttu-id="cdcf7-133">Wartość limitu czasu może być domyślnym limitem czasu ustawionym przez środowisko CLR lub wartość określoną przez hosta w wywołaniu metody [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cdcf7-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="cdcf7-134">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="cdcf7-135">`SetActionOnTimeout` jest zazwyczaj używany tylko w celu eskalacji zachowań.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="cdcf7-136">Na przykład host może określić, że przerwania wątku są włączane do przerwania wątku prosta, ale nie można określić przeciwieństwa.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="cdcf7-137">W poniższej tabeli opisano prawidłowe wartości `action` dla prawidłowych wartości `operation`.</span><span class="sxs-lookup"><span data-stu-id="cdcf7-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="cdcf7-138">Wartość `operation`</span><span class="sxs-lookup"><span data-stu-id="cdcf7-138">Value for `operation`</span></span>|<span data-ttu-id="cdcf7-139">Prawidłowe wartości dla `action`</span><span class="sxs-lookup"><span data-stu-id="cdcf7-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="cdcf7-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="cdcf7-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="cdcf7-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="cdcf7-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="cdcf7-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="cdcf7-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="cdcf7-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="cdcf7-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="cdcf7-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="cdcf7-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="cdcf7-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-145">-   eExitProcess</span></span><br /><span data-ttu-id="cdcf7-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="cdcf7-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="cdcf7-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="cdcf7-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="cdcf7-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="cdcf7-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="cdcf7-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="cdcf7-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="cdcf7-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="cdcf7-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="cdcf7-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-152">-   eExitProcess</span></span><br /><span data-ttu-id="cdcf7-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="cdcf7-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="cdcf7-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="cdcf7-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="cdcf7-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="cdcf7-156">OPR_ProcessExit</span></span>|<span data-ttu-id="cdcf7-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-157">-   eExitProcess</span></span><br /><span data-ttu-id="cdcf7-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="cdcf7-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="cdcf7-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="cdcf7-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="cdcf7-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdcf7-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdcf7-161">Requirements</span></span>  
 <span data-ttu-id="cdcf7-162">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdcf7-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdcf7-163">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cdcf7-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdcf7-164">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cdcf7-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdcf7-165">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdcf7-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcf7-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdcf7-166">See also</span></span>

- [<span data-ttu-id="cdcf7-167">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cdcf7-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="cdcf7-168">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cdcf7-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="cdcf7-169">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdcf7-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cdcf7-170">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdcf7-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
