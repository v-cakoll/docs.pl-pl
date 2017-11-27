---
title: "IHostCrst::SetSpinCount — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.SetSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19172c6d498e5066c102c642105d78d10b26212c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="7f810-102">IHostCrst::SetSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f810-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="7f810-103">Ustawia liczbę pokrętła dla bieżącego [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7f810-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f810-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f810-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f810-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f810-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="7f810-106">[in] Liczba nowych pokrętła dla bieżącego `IHostCrst` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7f810-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f810-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f810-107">Return Value</span></span>  
  
|<span data-ttu-id="7f810-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f810-108">HRESULT</span></span>|<span data-ttu-id="7f810-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7f810-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f810-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f810-110">S_OK</span></span>|<span data-ttu-id="7f810-111">`SetSpinCount`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f810-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="7f810-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f810-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f810-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7f810-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f810-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f810-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f810-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7f810-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f810-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f810-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f810-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7f810-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f810-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f810-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f810-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7f810-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f810-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f810-120">E_FAIL</span></span>|<span data-ttu-id="7f810-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7f810-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f810-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7f810-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f810-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f810-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f810-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f810-124">Remarks</span></span>  
 <span data-ttu-id="7f810-125">W systemach wieloprocesorowych, jeśli sekcja krytyczna reprezentowany przez bieżący `IHostCrst` wystąpienia jest niedostępna, obraca wątek wywołujący `dwSpinCount` razy przed wywołaniem [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semafora skojarzone sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="7f810-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="7f810-126">Jeśli sekcja krytyczna staje się wolnego podczas operacji pokrętła, wątek wywołujący pozwala uniknąć operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="7f810-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="7f810-127">Użycie `dwSpinCount` jest identyczny z użyciem parametru o takiej samej nazwie w Win32 `InitializeCriticalSectionAndSpinCount` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f810-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f810-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f810-128">Requirements</span></span>  
 <span data-ttu-id="7f810-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f810-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f810-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f810-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f810-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f810-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f810-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f810-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f810-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f810-133">See Also</span></span>  
 [<span data-ttu-id="7f810-134">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7f810-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7f810-135">IHostCrst — interfejs</span><span class="sxs-lookup"><span data-stu-id="7f810-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="7f810-136">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7f810-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
