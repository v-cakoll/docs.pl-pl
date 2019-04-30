---
title: IHostSyncManager::CreateRWLockReaderEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5b640093184e10ef9e3b895ce2328969a45ac9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696343"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="cbd6c-102">IHostSyncManager::CreateRWLockReaderEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbd6c-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="cbd6c-103">Tworzy obiekt zdarzeniach, resetowanego ręcznie do wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbd6c-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbd6c-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="cbd6c-106">[in] `true`, jeśli `ppEvent` powinien być zasygnalizowany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="cbd6c-107">[in] Plik cookie do skojarzenia z blokadą czytnika.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="cbd6c-108">[out] Wskaźnik na adres [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbd6c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbd6c-109">Return Value</span></span>  
  
|<span data-ttu-id="cbd6c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbd6c-110">HRESULT</span></span>|<span data-ttu-id="cbd6c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="cbd6c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbd6c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbd6c-112">S_OK</span></span>|<span data-ttu-id="cbd6c-113">`CreateRWLockReaderEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="cbd6c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbd6c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbd6c-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbd6c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbd6c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbd6c-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-117">The call timed out.</span></span>|  
|<span data-ttu-id="cbd6c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbd6c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbd6c-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbd6c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbd6c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbd6c-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbd6c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbd6c-122">E_FAIL</span></span>|<span data-ttu-id="cbd6c-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cbd6c-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbd6c-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cbd6c-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cbd6c-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cbd6c-127">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbd6c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbd6c-128">Remarks</span></span>  
 <span data-ttu-id="cbd6c-129">CLR wywołuje `CreateRWLockReaderEvent` można pobrać odwołania do `IHostManualEvent` wystąpienia do użycia w jego implementacja obiektu blokadę.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="cbd6c-130">Hosta można użyć pliku cookie do określenia, które zadania nie oczekuje na blokadę odczytu, badając [iclrsyncmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd6c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbd6c-131">Requirements</span></span>  
 <span data-ttu-id="cbd6c-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd6c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd6c-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cbd6c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbd6c-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbd6c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbd6c-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd6c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd6c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbd6c-136">See also</span></span>

- [<span data-ttu-id="cbd6c-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbd6c-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="cbd6c-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbd6c-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="cbd6c-139">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbd6c-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="cbd6c-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbd6c-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
