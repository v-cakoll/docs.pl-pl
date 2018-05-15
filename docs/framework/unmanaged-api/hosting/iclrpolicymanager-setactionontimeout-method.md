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
ms.openlocfilehash: cc1d16a2d57fea27c1c26fc55fbbfa9b74c25495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="e8e1b-102">ICLRPolicyManager::SetActionOnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8e1b-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="e8e1b-103">Określa akcję zasady, którą powinno mieć środowisko uruchomieniowe języka wspólnego (CLR), gdy upłynie limit czasu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8e1b-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8e1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8e1b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e8e1b-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący, który chcesz określić limit czasu akcji.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="e8e1b-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e8e1b-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e8e1b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e8e1b-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="e8e1b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e8e1b-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="e8e1b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8e1b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="e8e1b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8e1b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="e8e1b-112">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję zasad do wykonania, kiedy upłynie limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8e1b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8e1b-113">Return Value</span></span>  
  
|<span data-ttu-id="e8e1b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8e1b-114">HRESULT</span></span>|<span data-ttu-id="e8e1b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e8e1b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8e1b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8e1b-116">S_OK</span></span>|<span data-ttu-id="e8e1b-117">`SetActionOnTimeout` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e8e1b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8e1b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8e1b-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8e1b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8e1b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8e1b-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-121">The call timed out.</span></span>|  
|<span data-ttu-id="e8e1b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8e1b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8e1b-123">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8e1b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8e1b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8e1b-125">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8e1b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8e1b-126">E_FAIL</span></span>|<span data-ttu-id="e8e1b-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8e1b-128">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8e1b-129">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8e1b-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e8e1b-130">E_INVALIDARG</span></span>|<span data-ttu-id="e8e1b-131">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8e1b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8e1b-132">Remarks</span></span>  
 <span data-ttu-id="e8e1b-133">Wartość limitu czasu może być domyślny limit czasu ustawiony przez środowisko CLR lub wartość określonego przez hosta w wywołaniu [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="e8e1b-134">Nie wszystkie wartości działania zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e8e1b-135">`SetActionOnTimeout` zwykle służą tylko do eskalować zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="e8e1b-136">Na przykład host można określić, że wątek przerwań przekształcone niegrzeczny wątku przerwań, ale nie można określić odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e8e1b-137">W poniższej tabeli opisano poprawne `action` wartości prawidłowe `operation` wartości.</span><span class="sxs-lookup"><span data-stu-id="e8e1b-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="e8e1b-138">Wartość `operation`</span><span class="sxs-lookup"><span data-stu-id="e8e1b-138">Value for `operation`</span></span>|<span data-ttu-id="e8e1b-139">Prawidłowe wartości `action`</span><span class="sxs-lookup"><span data-stu-id="e8e1b-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e8e1b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8e1b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e8e1b-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8e1b-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e8e1b-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8e1b-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e8e1b-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8e1b-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8e1b-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8e1b-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8e1b-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-145">-   eExitProcess</span></span><br /><span data-ttu-id="e8e1b-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8e1b-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8e1b-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8e1b-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8e1b-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e8e1b-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e8e1b-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8e1b-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8e1b-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8e1b-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8e1b-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-152">-   eExitProcess</span></span><br /><span data-ttu-id="e8e1b-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8e1b-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8e1b-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8e1b-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8e1b-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e8e1b-156">OPR_ProcessExit</span></span>|<span data-ttu-id="e8e1b-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-157">-   eExitProcess</span></span><br /><span data-ttu-id="e8e1b-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8e1b-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8e1b-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8e1b-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8e1b-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8e1b-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8e1b-161">Requirements</span></span>  
 <span data-ttu-id="e8e1b-162">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e1b-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e1b-163">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8e1b-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8e1b-164">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8e1b-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8e1b-165">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e1b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e1b-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8e1b-166">See Also</span></span>  
 [<span data-ttu-id="e8e1b-167">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e8e1b-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e8e1b-168">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e8e1b-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e8e1b-169">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8e1b-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="e8e1b-170">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8e1b-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
