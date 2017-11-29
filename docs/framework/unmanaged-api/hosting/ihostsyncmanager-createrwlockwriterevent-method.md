---
title: "IHostSyncManager::CreateRWLockWriterEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c89dec681102f96f96f1d7f3e802ded0a2df7b4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="5c871-102">IHostSyncManager::CreateRWLockWriterEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c871-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="5c871-103">Tworzy obiekt zdarzenie z resetowaniem automatycznym dla implementacji blokadę.</span><span class="sxs-lookup"><span data-stu-id="5c871-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c871-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c871-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c871-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c871-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="5c871-106">[in] Plik cookie do skojarzenia z resetowaniem automatycznym zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c871-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="5c871-107">[out] Wskaźnik do adresu [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5c871-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c871-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c871-108">Return Value</span></span>  
  
|<span data-ttu-id="5c871-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c871-109">HRESULT</span></span>|<span data-ttu-id="5c871-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5c871-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c871-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c871-111">S_OK</span></span>|<span data-ttu-id="5c871-112">`CreateRWLockWriterEvent`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5c871-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="5c871-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c871-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c871-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5c871-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c871-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c871-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c871-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5c871-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c871-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c871-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c871-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5c871-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c871-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c871-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c871-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5c871-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c871-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c871-121">E_FAIL</span></span>|<span data-ttu-id="5c871-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5c871-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c871-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5c871-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c871-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c871-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c871-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5c871-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5c871-126">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5c871-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c871-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c871-127">Remarks</span></span>  
 <span data-ttu-id="5c871-128">Wywołania CLR `CreateRWLockWriterEvent` metodę, aby pobrać odwołanie do `IHostAutoEvent` wystąpienie do użycia w jej implementacja blokadę.</span><span class="sxs-lookup"><span data-stu-id="5c871-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="5c871-129">Host może używać określonego pliku cookie do określenia, zadania, które oczekują na blokadę przez wywołanie metody iteracji [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c871-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c871-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c871-130">Requirements</span></span>  
 <span data-ttu-id="5c871-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c871-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c871-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c871-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c871-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c871-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c871-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c871-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c871-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c871-135">See Also</span></span>  
 [<span data-ttu-id="5c871-136">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c871-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5c871-137">IHostAutoEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c871-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="5c871-138">IHostManualEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c871-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="5c871-139">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c871-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
