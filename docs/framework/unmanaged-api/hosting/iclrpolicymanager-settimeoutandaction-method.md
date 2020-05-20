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
ms.openlocfilehash: efd30ef04c148d5e098110efcb37e50f143884e4
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703429"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="8efec-102">ICLRPolicyManager::SetTimeoutAndAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="8efec-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="8efec-103">Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi operacja.</span><span class="sxs-lookup"><span data-stu-id="8efec-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8efec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8efec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8efec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8efec-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8efec-106">podczas Jedna z wartości [EClrOperation —](eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać ustawiony limit czasu i zasady `action` .</span><span class="sxs-lookup"><span data-stu-id="8efec-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="8efec-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8efec-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="8efec-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="8efec-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="8efec-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="8efec-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="8efec-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8efec-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="8efec-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8efec-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="8efec-112">podczas Nowa wartość limitu czasu (w milisekundach).</span><span class="sxs-lookup"><span data-stu-id="8efec-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="8efec-113">Wartość NIESKOŃCZONości `operation` nigdy nie przekracza limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="8efec-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="8efec-114">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję zasad, która powinna zostać podjęta przez środowisko CLR, gdy `operation` wystąpi.</span><span class="sxs-lookup"><span data-stu-id="8efec-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8efec-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8efec-115">Return Value</span></span>  
  
|<span data-ttu-id="8efec-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8efec-116">HRESULT</span></span>|<span data-ttu-id="8efec-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8efec-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8efec-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8efec-118">S_OK</span></span>|<span data-ttu-id="8efec-119">`SetTimeoutAndAction`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="8efec-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="8efec-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8efec-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8efec-121">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8efec-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8efec-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8efec-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8efec-123">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8efec-123">The call timed out.</span></span>|  
|<span data-ttu-id="8efec-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8efec-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8efec-125">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8efec-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8efec-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8efec-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8efec-127">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8efec-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8efec-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8efec-128">E_FAIL</span></span>|<span data-ttu-id="8efec-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8efec-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8efec-130">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="8efec-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8efec-131">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8efec-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8efec-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8efec-132">E_INVALIDARG</span></span>|<span data-ttu-id="8efec-133">Nie można ustawić limitu czasu dla określonego elementu `operation` lub podano nieprawidłową wartość dla elementu `action` .</span><span class="sxs-lookup"><span data-stu-id="8efec-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8efec-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8efec-134">Remarks</span></span>  
 <span data-ttu-id="8efec-135">`SetTimeoutAndAction`hermetyzuje możliwości metod [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) i [ICLRPolicyManager:: SetActionOnTimeout —](iclrpolicymanager-setactionontimeout-method.md) i można je wywołać zamiast wywołań sekwencyjnych do tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="8efec-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8efec-136">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="8efec-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="8efec-137">Zapoznaj się z sekcjami uwagi dla tych dwóch metod w celu uzyskania prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="8efec-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8efec-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8efec-138">Requirements</span></span>  
 <span data-ttu-id="8efec-139">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8efec-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8efec-140">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8efec-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8efec-141">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8efec-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8efec-142">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8efec-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efec-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8efec-143">See also</span></span>

- [<span data-ttu-id="8efec-144">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8efec-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8efec-145">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8efec-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8efec-146">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8efec-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8efec-147">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="8efec-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="8efec-148">ICLRPolicyManager:: SetTimeoutAndAction —</span><span class="sxs-lookup"><span data-stu-id="8efec-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
