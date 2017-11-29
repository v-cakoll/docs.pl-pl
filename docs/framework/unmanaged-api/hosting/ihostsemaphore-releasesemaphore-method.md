---
title: "IHostSemaphore::ReleaseSemaphore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.ReleaseSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06765d019d5443730656e7f4d6745bd8ad39ee00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="1dd56-102">IHostSemaphore::ReleaseSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dd56-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="1dd56-103">Zwiększa liczbę bieżącego [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) wystąpienia o określonej szerokości.</span><span class="sxs-lookup"><span data-stu-id="1dd56-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dd56-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dd56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dd56-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="1dd56-106">[in] Wartość, o którą należy zwiększyć liczbę bieżącego `IHostSemaphore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1dd56-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="1dd56-107">Ta wartość musi być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="1dd56-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="1dd56-108">[out] Wskaźnik do poprzedniego liczbę, lub wartość null, jeśli element wywołujący nie wymaga liczba w poprzednim.</span><span class="sxs-lookup"><span data-stu-id="1dd56-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd56-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1dd56-109">Return Value</span></span>  
  
|<span data-ttu-id="1dd56-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dd56-110">HRESULT</span></span>|<span data-ttu-id="1dd56-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd56-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dd56-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dd56-112">S_OK</span></span>|<span data-ttu-id="1dd56-113">`ReleaseSemaphore`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1dd56-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="1dd56-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dd56-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dd56-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1dd56-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dd56-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dd56-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dd56-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1dd56-117">The call timed out.</span></span>|  
|<span data-ttu-id="1dd56-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dd56-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dd56-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1dd56-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dd56-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dd56-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dd56-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1dd56-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dd56-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dd56-122">E_FAIL</span></span>|<span data-ttu-id="1dd56-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1dd56-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dd56-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1dd56-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dd56-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1dd56-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd56-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dd56-126">Remarks</span></span>  
 <span data-ttu-id="1dd56-127">Zazwyczaj wymaga środowiska CLR `ReleaseSemaphore` powiadomiono hosta, że zakończył przy użyciu zasobów, należy wprowadzić wartość 1 w przypadku `lReleaseCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="1dd56-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd56-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dd56-128">Requirements</span></span>  
 <span data-ttu-id="1dd56-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd56-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd56-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1dd56-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd56-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dd56-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd56-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd56-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd56-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dd56-133">See Also</span></span>  
 [<span data-ttu-id="1dd56-134">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd56-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1dd56-135">IHostAutoEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd56-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="1dd56-136">IHostManualEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd56-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="1dd56-137">IHostSemaphore — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd56-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="1dd56-138">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd56-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
