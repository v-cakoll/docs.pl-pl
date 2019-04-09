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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093504"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="5a9dd-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a9dd-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="5a9dd-103">Ustawia bieżący [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a9dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a9dd-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5a9dd-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5a9dd-105">Return Value</span></span>  
  
|<span data-ttu-id="5a9dd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a9dd-106">HRESULT</span></span>|<span data-ttu-id="5a9dd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5a9dd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a9dd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a9dd-108">S_OK</span></span>|`Set` <span data-ttu-id="5a9dd-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-109">returned successfully.</span></span>|  
|<span data-ttu-id="5a9dd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a9dd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a9dd-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a9dd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a9dd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a9dd-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-113">The call timed out.</span></span>|  
|<span data-ttu-id="5a9dd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a9dd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a9dd-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a9dd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a9dd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a9dd-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a9dd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a9dd-118">E_FAIL</span></span>|<span data-ttu-id="5a9dd-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a9dd-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a9dd-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5a9dd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a9dd-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a9dd-122">Requirements</span></span>  
 <span data-ttu-id="5a9dd-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a9dd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a9dd-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a9dd-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a9dd-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a9dd-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5a9dd-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5a9dd-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a9dd-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a9dd-127">See also</span></span>

- [<span data-ttu-id="5a9dd-128">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9dd-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5a9dd-129">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9dd-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="5a9dd-130">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9dd-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="5a9dd-131">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9dd-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="5a9dd-132">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9dd-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
