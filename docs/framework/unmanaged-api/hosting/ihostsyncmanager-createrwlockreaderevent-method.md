---
title: "IHostSyncManager::CreateRWLockReaderEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b583e7b5dd1a83ecb891591c25802ae257ad7c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="221da-102">IHostSyncManager::CreateRWLockReaderEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="221da-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="221da-103">Tworzy obiekt zdarzenia resetowania ręcznego wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="221da-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="221da-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="221da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="221da-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="221da-106">[in] `true`, jeśli `ppEvent` sygnałowego; w przeciwnym razie wartość powinna być `false`.</span><span class="sxs-lookup"><span data-stu-id="221da-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="221da-107">[in] Plik cookie do skojarzenia z blokada czytnika.</span><span class="sxs-lookup"><span data-stu-id="221da-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="221da-108">[out] Wskaźnik do adresu [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="221da-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="221da-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="221da-109">Return Value</span></span>  
  
|<span data-ttu-id="221da-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="221da-110">HRESULT</span></span>|<span data-ttu-id="221da-111">Opis</span><span class="sxs-lookup"><span data-stu-id="221da-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="221da-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="221da-112">S_OK</span></span>|<span data-ttu-id="221da-113">`CreateRWLockReaderEvent`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="221da-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="221da-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="221da-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="221da-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="221da-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="221da-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="221da-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="221da-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="221da-117">The call timed out.</span></span>|  
|<span data-ttu-id="221da-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="221da-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="221da-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="221da-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="221da-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="221da-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="221da-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="221da-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="221da-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="221da-122">E_FAIL</span></span>|<span data-ttu-id="221da-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="221da-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="221da-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="221da-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="221da-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="221da-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="221da-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="221da-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="221da-127">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="221da-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="221da-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="221da-128">Remarks</span></span>  
 <span data-ttu-id="221da-129">Wywołania CLR `CreateRWLockReaderEvent` można pobrać odwołania do `IHostManualEvent` wystąpienie do użycia w jej implementacja blokadę.</span><span class="sxs-lookup"><span data-stu-id="221da-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="221da-130">Host może używać pliku cookie do określenia, zadania, które oczekują na blokada czytnika badając [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="221da-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="221da-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="221da-131">Requirements</span></span>  
 <span data-ttu-id="221da-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="221da-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="221da-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="221da-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="221da-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="221da-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="221da-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="221da-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221da-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="221da-136">See Also</span></span>  
 [<span data-ttu-id="221da-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="221da-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="221da-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="221da-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="221da-139">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="221da-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="221da-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="221da-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
