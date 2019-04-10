---
title: IHostSyncManager::CreateRWLockWriterEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e994cf5c68871d6e81d53ac522259bc973c173ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223618"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="291b1-102">IHostSyncManager::CreateRWLockWriterEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="291b1-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="291b1-103">Tworzy obiekt zdarzenie z resetowaniem automatycznym do wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="291b1-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="291b1-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="291b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="291b1-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="291b1-106">[in] Plik cookie do skojarzenia z resetowaniem automatycznym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="291b1-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="291b1-107">[out] Wskaźnik na adres [ihostautoevent —](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="291b1-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="291b1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="291b1-108">Return Value</span></span>  
  
|<span data-ttu-id="291b1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="291b1-109">HRESULT</span></span>|<span data-ttu-id="291b1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="291b1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="291b1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="291b1-111">S_OK</span></span>|`CreateRWLockWriterEvent` <span data-ttu-id="291b1-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="291b1-112">returned successfully.</span></span>|  
|<span data-ttu-id="291b1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="291b1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="291b1-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="291b1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="291b1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="291b1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="291b1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="291b1-116">The call timed out.</span></span>|  
|<span data-ttu-id="291b1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="291b1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="291b1-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="291b1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="291b1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="291b1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="291b1-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="291b1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="291b1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="291b1-121">E_FAIL</span></span>|<span data-ttu-id="291b1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="291b1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="291b1-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="291b1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="291b1-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="291b1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="291b1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="291b1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="291b1-126">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="291b1-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="291b1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="291b1-127">Remarks</span></span>  
 <span data-ttu-id="291b1-128">CLR wywołuje `CreateRWLockWriterEvent` metodę, aby pobrać odwołanie do `IHostAutoEvent` wystąpienia do użycia w jego implementacja obiektu blokadę.</span><span class="sxs-lookup"><span data-stu-id="291b1-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="291b1-129">Hosta można użyć określonego pliku cookie do określenia, które zadania nie oczekuje na blokadę przez wywołanie metody iteracji [iclrsyncmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="291b1-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="291b1-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="291b1-130">Requirements</span></span>  
 <span data-ttu-id="291b1-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="291b1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="291b1-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="291b1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="291b1-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="291b1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="291b1-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="291b1-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="291b1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="291b1-135">See also</span></span>

- [<span data-ttu-id="291b1-136">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="291b1-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="291b1-137">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="291b1-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="291b1-138">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="291b1-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="291b1-139">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="291b1-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
