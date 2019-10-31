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
ms.openlocfilehash: b3778e12dd96d4f4653633252e13469601c4879d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139437"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="83531-102">IHostSyncManager::CreateAutoEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="83531-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="83531-103">Tworzy obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="83531-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83531-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83531-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83531-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83531-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="83531-106">określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) zaimplementowanego przez hosta lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="83531-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83531-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83531-107">Return Value</span></span>  
  
|<span data-ttu-id="83531-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83531-108">HRESULT</span></span>|<span data-ttu-id="83531-109">Opis</span><span class="sxs-lookup"><span data-stu-id="83531-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83531-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83531-110">S_OK</span></span>|<span data-ttu-id="83531-111">`CreateAutoEvent` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="83531-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="83531-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83531-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83531-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="83531-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83531-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83531-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83531-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="83531-115">The call timed out.</span></span>|  
|<span data-ttu-id="83531-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83531-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83531-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="83531-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83531-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83531-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83531-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="83531-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83531-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83531-120">E_FAIL</span></span>|<span data-ttu-id="83531-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="83531-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83531-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="83531-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83531-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83531-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="83531-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="83531-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="83531-125">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="83531-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83531-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83531-126">Remarks</span></span>  
 <span data-ttu-id="83531-127">`CreateAutoEvent` tworzy obiekt automatycznego zdarzenia, którego stan jest automatycznie zmieniany na niesygnalizujący po wydaniu oczekującego wątku.</span><span class="sxs-lookup"><span data-stu-id="83531-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="83531-128">Ta metoda odzwierciedla funkcję `CreateEvent` Win32 z wartością `false` określoną dla parametru `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="83531-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83531-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83531-129">Requirements</span></span>  
 <span data-ttu-id="83531-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83531-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83531-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83531-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83531-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83531-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83531-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83531-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83531-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83531-134">See also</span></span>

- [<span data-ttu-id="83531-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="83531-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="83531-136">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="83531-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="83531-137">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="83531-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="83531-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="83531-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
