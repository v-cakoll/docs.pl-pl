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
ms.openlocfilehash: c375fdffacccb27c20878c4e6adef9dd947148e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435527"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="520fc-102">ICLRPolicyManager::SetTimeoutAndAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="520fc-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="520fc-103">Ustawia wartość limitu czasu dla określonej operacji, a następnie określa działanie zasad, które powinno mieć środowisko uruchomieniowe języka wspólnego (CLR), gdy operacja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="520fc-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="520fc-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="520fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="520fc-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="520fc-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący operację, dla którego można ustawić limitu czasu i zasad `action`.</span><span class="sxs-lookup"><span data-stu-id="520fc-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="520fc-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="520fc-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="520fc-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="520fc-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="520fc-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="520fc-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="520fc-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="520fc-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="520fc-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="520fc-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="520fc-112">[in] Nowa wartość limitu czasu, w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="520fc-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="520fc-113">Wartość NIESKOŃCZONA przyczyny `operation` nigdy nie kończy się.</span><span class="sxs-lookup"><span data-stu-id="520fc-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="520fc-114">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję zasad, że środowisko CLR powinien wykonać, gdy `operation` występuje.</span><span class="sxs-lookup"><span data-stu-id="520fc-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="520fc-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="520fc-115">Return Value</span></span>  
  
|<span data-ttu-id="520fc-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="520fc-116">HRESULT</span></span>|<span data-ttu-id="520fc-117">Opis</span><span class="sxs-lookup"><span data-stu-id="520fc-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="520fc-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="520fc-118">S_OK</span></span>|<span data-ttu-id="520fc-119">`SetTimeoutAndAction` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="520fc-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="520fc-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="520fc-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="520fc-121">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="520fc-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="520fc-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="520fc-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="520fc-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="520fc-123">The call timed out.</span></span>|  
|<span data-ttu-id="520fc-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="520fc-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="520fc-125">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="520fc-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="520fc-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="520fc-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="520fc-127">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="520fc-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="520fc-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="520fc-128">E_FAIL</span></span>|<span data-ttu-id="520fc-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="520fc-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="520fc-130">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="520fc-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="520fc-131">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="520fc-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="520fc-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="520fc-132">E_INVALIDARG</span></span>|<span data-ttu-id="520fc-133">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `action`.</span><span class="sxs-lookup"><span data-stu-id="520fc-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="520fc-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="520fc-134">Remarks</span></span>  
 <span data-ttu-id="520fc-135">`SetTimeoutAndAction` hermetyzuje możliwości [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) i [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metod i może zostać wywołana zamiast kolejne wywołania te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="520fc-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="520fc-136">Nie wszystkie wartości działania zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="520fc-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="520fc-137">Zobacz sekcje uwag w tematach te dwie metody prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="520fc-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520fc-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="520fc-138">Requirements</span></span>  
 <span data-ttu-id="520fc-139">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="520fc-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="520fc-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="520fc-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="520fc-141">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="520fc-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="520fc-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="520fc-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520fc-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="520fc-143">See Also</span></span>  
 [<span data-ttu-id="520fc-144">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="520fc-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="520fc-145">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="520fc-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="520fc-146">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="520fc-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="520fc-147">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="520fc-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="520fc-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="520fc-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
