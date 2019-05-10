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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d99f4f0615e7d25991b37030b7cb609985192f
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910665"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="bda16-102">ICLRPolicyManager::SetActionOnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="bda16-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="bda16-103">Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy upłynie limit czasu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="bda16-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bda16-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bda16-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="bda16-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący, do których chcesz określić akcję limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="bda16-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="bda16-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="bda16-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="bda16-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="bda16-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="bda16-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="bda16-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="bda16-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bda16-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="bda16-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bda16-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="bda16-112">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję zasad do wykonania, kiedy upłynie limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="bda16-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bda16-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bda16-113">Return Value</span></span>  
  
|<span data-ttu-id="bda16-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bda16-114">HRESULT</span></span>|<span data-ttu-id="bda16-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bda16-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bda16-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="bda16-116">S_OK</span></span>|<span data-ttu-id="bda16-117">`SetActionOnTimeout` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="bda16-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="bda16-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bda16-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bda16-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bda16-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bda16-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bda16-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bda16-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bda16-121">The call timed out.</span></span>|  
|<span data-ttu-id="bda16-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bda16-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bda16-123">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="bda16-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bda16-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bda16-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bda16-125">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bda16-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bda16-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bda16-126">E_FAIL</span></span>|<span data-ttu-id="bda16-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bda16-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bda16-128">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bda16-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bda16-129">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bda16-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bda16-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bda16-130">E_INVALIDARG</span></span>|<span data-ttu-id="bda16-131">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="bda16-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bda16-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bda16-132">Remarks</span></span>  
 <span data-ttu-id="bda16-133">Wartość limitu czasu może być domyślny limit czasu ustawiony przez środowisko CLR, lub wartość określoną przez hosta w wywołaniu [iclrpolicymanager::setTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bda16-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="bda16-134">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu w operacjach aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="bda16-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="bda16-135">`SetActionOnTimeout` zwykle jest używana tylko w celu Eskalowanie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bda16-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="bda16-136">Na przykład host można określić, czy przerwanie wątku przekształcone prosta wątku przerwań, ale nie można określić odwrotny.</span><span class="sxs-lookup"><span data-stu-id="bda16-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="bda16-137">W poniższej tabeli opisano prawidłowe `action` wartości prawidłowe `operation` wartości.</span><span class="sxs-lookup"><span data-stu-id="bda16-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="bda16-138">Wartość `operation`</span><span class="sxs-lookup"><span data-stu-id="bda16-138">Value for `operation`</span></span>|<span data-ttu-id="bda16-139">Prawidłowe wartości `action`</span><span class="sxs-lookup"><span data-stu-id="bda16-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="bda16-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bda16-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="bda16-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bda16-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="bda16-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="bda16-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="bda16-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bda16-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="bda16-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bda16-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="bda16-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-145">-   eExitProcess</span></span><br /><span data-ttu-id="bda16-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="bda16-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bda16-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bda16-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="bda16-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="bda16-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="bda16-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bda16-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="bda16-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bda16-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="bda16-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-152">-   eExitProcess</span></span><br /><span data-ttu-id="bda16-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="bda16-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bda16-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bda16-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="bda16-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="bda16-156">OPR_ProcessExit</span></span>|<span data-ttu-id="bda16-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-157">-   eExitProcess</span></span><br /><span data-ttu-id="bda16-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="bda16-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bda16-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bda16-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bda16-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bda16-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bda16-161">Requirements</span></span>  
 <span data-ttu-id="bda16-162">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bda16-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda16-163">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bda16-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bda16-164">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bda16-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bda16-165">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda16-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda16-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bda16-166">See also</span></span>

- [<span data-ttu-id="bda16-167">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bda16-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="bda16-168">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bda16-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="bda16-169">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="bda16-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="bda16-170">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bda16-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
