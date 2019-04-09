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
ms.openlocfilehash: 30ab869ed6b06f5c9e53d819e20d3307ccc0e8f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109931"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="f71f8-102">ICLRPolicyManager::SetActionOnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="f71f8-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="f71f8-103">Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy upłynie limit czasu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="f71f8-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f71f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f71f8-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f71f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f71f8-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="f71f8-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący, do których chcesz określić akcję limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f71f8-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="f71f8-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f71f8-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="f71f8-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="f71f8-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="f71f8-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="f71f8-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="f71f8-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f71f8-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="f71f8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f71f8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="f71f8-112">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję zasad do wykonania, kiedy upłynie limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="f71f8-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f71f8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f71f8-113">Return Value</span></span>  
  
|<span data-ttu-id="f71f8-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f71f8-114">HRESULT</span></span>|<span data-ttu-id="f71f8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f71f8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f71f8-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f71f8-116">S_OK</span></span>|`SetActionOnTimeout` <span data-ttu-id="f71f8-117">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f71f8-117">returned successfully.</span></span>|  
|<span data-ttu-id="f71f8-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f71f8-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f71f8-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f71f8-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f71f8-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f71f8-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f71f8-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f71f8-121">The call timed out.</span></span>|  
|<span data-ttu-id="f71f8-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f71f8-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f71f8-123">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="f71f8-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f71f8-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f71f8-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f71f8-125">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f71f8-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f71f8-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f71f8-126">E_FAIL</span></span>|<span data-ttu-id="f71f8-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f71f8-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f71f8-128">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f71f8-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f71f8-129">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f71f8-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f71f8-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f71f8-130">E_INVALIDARG</span></span>|<span data-ttu-id="f71f8-131">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="f71f8-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f71f8-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f71f8-132">Remarks</span></span>  
 <span data-ttu-id="f71f8-133">Wartość limitu czasu może być domyślny limit czasu ustawiony przez środowisko CLR, lub wartość określoną przez hosta w wywołaniu [iclrpolicymanager::setTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f71f8-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="f71f8-134">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu w operacjach aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="f71f8-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> `SetActionOnTimeout` <span data-ttu-id="f71f8-135">zwykle jest używana tylko w celu Eskalowanie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f71f8-135">is typically used only to escalate behavior.</span></span> <span data-ttu-id="f71f8-136">Na przykład host można określić, czy przerwanie wątku przekształcone prosta wątku przerwań, ale nie można określić odwrotny.</span><span class="sxs-lookup"><span data-stu-id="f71f8-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="f71f8-137">W poniższej tabeli opisano prawidłowe `action` wartości prawidłowe `operation` wartości.</span><span class="sxs-lookup"><span data-stu-id="f71f8-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="f71f8-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="f71f8-138">Value for</span></span> `operation`|<span data-ttu-id="f71f8-139">Prawidłowe wartości</span><span class="sxs-lookup"><span data-stu-id="f71f8-139">Valid values for</span></span> `action`|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="f71f8-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f71f8-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="f71f8-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f71f8-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="f71f8-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="f71f8-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="f71f8-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f71f8-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="f71f8-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f71f8-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="f71f8-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-145">-   eExitProcess</span></span><br /><span data-ttu-id="f71f8-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="f71f8-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f71f8-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f71f8-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="f71f8-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="f71f8-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="f71f8-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f71f8-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="f71f8-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f71f8-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="f71f8-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-152">-   eExitProcess</span></span><br /><span data-ttu-id="f71f8-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="f71f8-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f71f8-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f71f8-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="f71f8-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="f71f8-156">OPR_ProcessExit</span></span>|<span data-ttu-id="f71f8-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-157">-   eExitProcess</span></span><br /><span data-ttu-id="f71f8-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="f71f8-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f71f8-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f71f8-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f71f8-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f71f8-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f71f8-161">Requirements</span></span>  
 <span data-ttu-id="f71f8-162">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f71f8-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f71f8-163">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f71f8-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f71f8-164">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f71f8-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f71f8-165">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f71f8-165">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f71f8-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f71f8-166">See also</span></span>

- [<span data-ttu-id="f71f8-167">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f71f8-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="f71f8-168">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f71f8-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="f71f8-169">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f71f8-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f71f8-170">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f71f8-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
