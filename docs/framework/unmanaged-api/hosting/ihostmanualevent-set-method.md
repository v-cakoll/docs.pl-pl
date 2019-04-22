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
ms.openlocfilehash: 674745636033f42eb8fb67babf6f5a3f013491c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093504"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="bf33b-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf33b-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="bf33b-103">Ustawia bieżący [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="bf33b-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf33b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf33b-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bf33b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf33b-105">Return Value</span></span>  
  
|<span data-ttu-id="bf33b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf33b-106">HRESULT</span></span>|<span data-ttu-id="bf33b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf33b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf33b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf33b-108">S_OK</span></span>|<span data-ttu-id="bf33b-109">`Set` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="bf33b-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="bf33b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf33b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf33b-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bf33b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf33b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf33b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf33b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bf33b-113">The call timed out.</span></span>|  
|<span data-ttu-id="bf33b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf33b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf33b-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="bf33b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf33b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf33b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf33b-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bf33b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf33b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf33b-118">E_FAIL</span></span>|<span data-ttu-id="bf33b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bf33b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf33b-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bf33b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf33b-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf33b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf33b-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf33b-122">Requirements</span></span>  
 <span data-ttu-id="bf33b-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf33b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf33b-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf33b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf33b-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf33b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf33b-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf33b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf33b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf33b-127">See also</span></span>

- [<span data-ttu-id="bf33b-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf33b-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="bf33b-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf33b-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="bf33b-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf33b-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="bf33b-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf33b-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="bf33b-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf33b-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
