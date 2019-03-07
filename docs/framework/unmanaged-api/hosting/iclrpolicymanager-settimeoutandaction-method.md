---
title: ICLRPolicyManager::SetTimeoutAndAction — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ea97084351bdc0a9dbd85d7a6a38a34acffaac8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489283"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="a9179-102">ICLRPolicyManager::SetTimeoutAndAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9179-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="a9179-103">Ustawia wartość limitu czasu dla określonej operacji i określa działanie zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy operacja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="a9179-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9179-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9179-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9179-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9179-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a9179-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazując operacji, dla którego ma zostać ustawiony limit czasu i zasady `action`.</span><span class="sxs-lookup"><span data-stu-id="a9179-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="a9179-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a9179-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a9179-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a9179-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="a9179-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a9179-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="a9179-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9179-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="a9179-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9179-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="a9179-112">[in] Nowa wartość limitu czasu, w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="a9179-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="a9179-113">Wartość powoduje NIESKOŃCZONĄ `operation` nigdy do niej limit czasu.</span><span class="sxs-lookup"><span data-stu-id="a9179-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="a9179-114">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazując działanie zasad, że środowisko CLR powinien wykonać, gdy `operation` występuje.</span><span class="sxs-lookup"><span data-stu-id="a9179-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9179-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9179-115">Return Value</span></span>  
  
|<span data-ttu-id="a9179-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9179-116">HRESULT</span></span>|<span data-ttu-id="a9179-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a9179-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9179-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9179-118">S_OK</span></span>|<span data-ttu-id="a9179-119">`SetTimeoutAndAction` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a9179-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="a9179-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9179-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9179-121">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9179-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9179-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9179-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9179-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9179-123">The call timed out.</span></span>|  
|<span data-ttu-id="a9179-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9179-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9179-125">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a9179-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9179-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9179-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9179-127">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a9179-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9179-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9179-128">E_FAIL</span></span>|<span data-ttu-id="a9179-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a9179-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9179-130">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a9179-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9179-131">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9179-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9179-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a9179-132">E_INVALIDARG</span></span>|<span data-ttu-id="a9179-133">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `action`.</span><span class="sxs-lookup"><span data-stu-id="a9179-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9179-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9179-134">Remarks</span></span>  
 <span data-ttu-id="a9179-135">`SetTimeoutAndAction` hermetyzuje możliwości [iclrpolicymanager::setTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) i [iclrpolicymanager::setactionontimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metod i może być wywoływana zamiast kolejnych wywołań do tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="a9179-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9179-136">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu w operacjach aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="a9179-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="a9179-137">Zobacz sekcje uwag w tematach tych dwóch metod prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="a9179-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9179-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9179-138">Requirements</span></span>  
 <span data-ttu-id="a9179-139">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9179-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9179-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9179-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9179-141">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9179-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9179-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9179-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9179-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9179-143">See also</span></span>
- [<span data-ttu-id="a9179-144">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a9179-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a9179-145">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a9179-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="a9179-146">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9179-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="a9179-147">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="a9179-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="a9179-148">Iclrpolicymanager::settimeoutandaction —</span><span class="sxs-lookup"><span data-stu-id="a9179-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
