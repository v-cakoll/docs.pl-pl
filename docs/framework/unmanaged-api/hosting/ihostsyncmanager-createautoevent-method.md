---
title: IHostSyncManager::CreateAutoEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9c91a982a5f3d28b43a301f961601485639bb91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180644"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="b9b57-102">IHostSyncManager::CreateAutoEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="b9b57-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="b9b57-103">Tworzy obiekt zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="b9b57-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9b57-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9b57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9b57-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="b9b57-106">[out] Wskaźnik na adres [ihostautoevent —](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia implementowane przez hosta lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b9b57-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9b57-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9b57-107">Return Value</span></span>  
  
|<span data-ttu-id="b9b57-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9b57-108">HRESULT</span></span>|<span data-ttu-id="b9b57-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b57-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9b57-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9b57-110">S_OK</span></span>|<span data-ttu-id="b9b57-111">`CreateAutoEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b9b57-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b9b57-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9b57-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9b57-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9b57-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9b57-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9b57-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9b57-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9b57-115">The call timed out.</span></span>|  
|<span data-ttu-id="b9b57-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9b57-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9b57-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b9b57-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9b57-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9b57-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9b57-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b9b57-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9b57-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9b57-120">E_FAIL</span></span>|<span data-ttu-id="b9b57-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b9b57-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9b57-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b9b57-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9b57-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9b57-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9b57-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b9b57-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b9b57-125">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b9b57-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b57-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9b57-126">Remarks</span></span>  
 <span data-ttu-id="b9b57-127">`CreateAutoEvent` Tworzy obiekt zdarzenia automatycznie, którego stan jest automatycznie zmieniona zasygnalizowane po udostępnieniu wątków oczekujących.</span><span class="sxs-lookup"><span data-stu-id="b9b57-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="b9b57-128">Ta metoda odzwierciedla Win32 `CreateEvent` funkcji z wartością `false` określony dla `bManualReset` parametru</span><span class="sxs-lookup"><span data-stu-id="b9b57-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b57-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9b57-129">Requirements</span></span>  
 <span data-ttu-id="b9b57-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b57-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b57-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9b57-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9b57-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9b57-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9b57-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b57-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b57-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9b57-134">See also</span></span>

- [<span data-ttu-id="b9b57-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9b57-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b9b57-136">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9b57-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b9b57-137">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9b57-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="b9b57-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9b57-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
