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
ms.openlocfilehash: c1c40b27cd2899b5c3142364958b18144b8d4fee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709705"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="74ce2-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="74ce2-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="74ce2-103">Ustawia bieżący [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="74ce2-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ce2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74ce2-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="74ce2-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="74ce2-105">Return Value</span></span>  
  
|<span data-ttu-id="74ce2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74ce2-106">HRESULT</span></span>|<span data-ttu-id="74ce2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="74ce2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74ce2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="74ce2-108">S_OK</span></span>|<span data-ttu-id="74ce2-109">`Set` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="74ce2-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="74ce2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74ce2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74ce2-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74ce2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74ce2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74ce2-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce2-113">The call timed out.</span></span>|  
|<span data-ttu-id="74ce2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74ce2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74ce2-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="74ce2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74ce2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74ce2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74ce2-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="74ce2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74ce2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74ce2-118">E_FAIL</span></span>|<span data-ttu-id="74ce2-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="74ce2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74ce2-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="74ce2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74ce2-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74ce2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74ce2-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74ce2-122">Requirements</span></span>  
 <span data-ttu-id="74ce2-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ce2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ce2-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74ce2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74ce2-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74ce2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74ce2-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ce2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ce2-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74ce2-127">See also</span></span>
- [<span data-ttu-id="74ce2-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce2-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="74ce2-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce2-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="74ce2-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce2-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="74ce2-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce2-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="74ce2-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce2-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
