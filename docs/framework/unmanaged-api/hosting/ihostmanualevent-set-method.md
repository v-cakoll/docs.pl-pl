---
title: IHostManualEvent::Set — Metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3756ed3bc7863411849b9d733da816e567a86628
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767304"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="ed17c-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed17c-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="ed17c-103">Ustawia bieżący [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="ed17c-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed17c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed17c-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ed17c-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed17c-105">Return Value</span></span>  
  
|<span data-ttu-id="ed17c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed17c-106">HRESULT</span></span>|<span data-ttu-id="ed17c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ed17c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed17c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed17c-108">S_OK</span></span>|<span data-ttu-id="ed17c-109">`Set` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ed17c-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="ed17c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed17c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed17c-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ed17c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed17c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed17c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed17c-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ed17c-113">The call timed out.</span></span>|  
|<span data-ttu-id="ed17c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed17c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed17c-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ed17c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed17c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed17c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed17c-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ed17c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed17c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed17c-118">E_FAIL</span></span>|<span data-ttu-id="ed17c-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ed17c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed17c-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ed17c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed17c-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed17c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed17c-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed17c-122">Requirements</span></span>  
 <span data-ttu-id="ed17c-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed17c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed17c-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed17c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed17c-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed17c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed17c-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed17c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed17c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed17c-127">See also</span></span>

- [<span data-ttu-id="ed17c-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed17c-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ed17c-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed17c-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ed17c-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed17c-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="ed17c-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed17c-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="ed17c-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed17c-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
