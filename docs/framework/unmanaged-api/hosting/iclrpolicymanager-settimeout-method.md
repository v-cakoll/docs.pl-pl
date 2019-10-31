---
title: ICLRPolicyManager::SetTimeout — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140750"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="e0972-102">ICLRPolicyManager::SetTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0972-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="e0972-103">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="e0972-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0972-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0972-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0972-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0972-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e0972-106">podczas Jedna z wartości [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , wskazująca na operację środowiska uruchomieniowego języka wspólnego (CLR), dla którego ma zostać ustawiony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="e0972-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="e0972-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e0972-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="e0972-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e0972-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="e0972-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e0972-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="e0972-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0972-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="e0972-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0972-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="e0972-112">podczas Nowa wartość limitu czasu (w milisekundach).</span><span class="sxs-lookup"><span data-stu-id="e0972-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="e0972-113">Wartość NIESKOŃCZONość powoduje, że nigdy nie upłynął limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="e0972-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0972-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0972-114">Return Value</span></span>  
  
|<span data-ttu-id="e0972-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0972-115">HRESULT</span></span>|<span data-ttu-id="e0972-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e0972-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0972-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0972-117">S_OK</span></span>|<span data-ttu-id="e0972-118">`SetTimeout` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e0972-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e0972-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0972-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0972-120">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e0972-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0972-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0972-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0972-122">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e0972-122">The call timed out.</span></span>|  
|<span data-ttu-id="e0972-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0972-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0972-124">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e0972-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0972-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0972-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0972-126">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e0972-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0972-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0972-127">E_FAIL</span></span>|<span data-ttu-id="e0972-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e0972-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0972-129">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="e0972-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0972-130">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0972-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0972-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e0972-131">E_INVALIDARG</span></span>|<span data-ttu-id="e0972-132">Nie można ustawić limitu czasu dla określonego `operation`lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="e0972-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0972-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0972-133">Requirements</span></span>  
 <span data-ttu-id="e0972-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0972-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0972-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0972-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0972-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0972-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0972-137">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0972-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0972-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0972-138">See also</span></span>

- [<span data-ttu-id="e0972-139">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e0972-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="e0972-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0972-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e0972-141">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0972-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
