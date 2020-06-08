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
ms.openlocfilehash: 02e836601be72d54f561e077cd3c466470bafb25
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504098"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="8cfee-102">ICLRPolicyManager::SetTimeoutAndAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="8cfee-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="8cfee-103">Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi operacja.</span><span class="sxs-lookup"><span data-stu-id="8cfee-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cfee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cfee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cfee-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8cfee-106">podczas Jedna z wartości [EClrOperation —](eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać ustawiony limit czasu i zasady `action` .</span><span class="sxs-lookup"><span data-stu-id="8cfee-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="8cfee-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8cfee-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="8cfee-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="8cfee-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="8cfee-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="8cfee-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="8cfee-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8cfee-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="8cfee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8cfee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="8cfee-112">podczas Nowa wartość limitu czasu (w milisekundach).</span><span class="sxs-lookup"><span data-stu-id="8cfee-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="8cfee-113">Wartość NIESKOŃCZONości `operation` nigdy nie przekracza limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="8cfee-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="8cfee-114">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję zasad, która powinna zostać podjęta przez środowisko CLR, gdy `operation` wystąpi.</span><span class="sxs-lookup"><span data-stu-id="8cfee-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cfee-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8cfee-115">Return Value</span></span>  
  
|<span data-ttu-id="8cfee-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cfee-116">HRESULT</span></span>|<span data-ttu-id="8cfee-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8cfee-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cfee-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cfee-118">S_OK</span></span>|<span data-ttu-id="8cfee-119">`SetTimeoutAndAction`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="8cfee-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="8cfee-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cfee-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cfee-121">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8cfee-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8cfee-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8cfee-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8cfee-123">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8cfee-123">The call timed out.</span></span>|  
|<span data-ttu-id="8cfee-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8cfee-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8cfee-125">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8cfee-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8cfee-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8cfee-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8cfee-127">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8cfee-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8cfee-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cfee-128">E_FAIL</span></span>|<span data-ttu-id="8cfee-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8cfee-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cfee-130">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="8cfee-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8cfee-131">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8cfee-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8cfee-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8cfee-132">E_INVALIDARG</span></span>|<span data-ttu-id="8cfee-133">Nie można ustawić limitu czasu dla określonego elementu `operation` lub podano nieprawidłową wartość dla elementu `action` .</span><span class="sxs-lookup"><span data-stu-id="8cfee-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cfee-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cfee-134">Remarks</span></span>  
 <span data-ttu-id="8cfee-135">`SetTimeoutAndAction`hermetyzuje możliwości metod [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) i [ICLRPolicyManager:: SetActionOnTimeout —](iclrpolicymanager-setactionontimeout-method.md) i można je wywołać zamiast wywołań sekwencyjnych do tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="8cfee-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8cfee-136">Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="8cfee-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="8cfee-137">Zapoznaj się z sekcjami uwagi dla tych dwóch metod w celu uzyskania prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="8cfee-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cfee-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cfee-138">Requirements</span></span>  
 <span data-ttu-id="8cfee-139">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cfee-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfee-140">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8cfee-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cfee-141">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8cfee-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cfee-142">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfee-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfee-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cfee-143">See also</span></span>

- [<span data-ttu-id="8cfee-144">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8cfee-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8cfee-145">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8cfee-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8cfee-146">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8cfee-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8cfee-147">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="8cfee-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="8cfee-148">ICLRPolicyManager:: SetTimeoutAndAction —</span><span class="sxs-lookup"><span data-stu-id="8cfee-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
