---
title: IHostManualEvent::Reset — Metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b3de70e6bdecba6370174ee825d2dec7c14270e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148567"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="b223d-102">IHostManualEvent::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="b223d-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="b223d-103">Przywraca bieżące [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="b223d-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b223d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b223d-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b223d-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b223d-105">Return Value</span></span>  
  
|<span data-ttu-id="b223d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b223d-106">HRESULT</span></span>|<span data-ttu-id="b223d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b223d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b223d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b223d-108">S_OK</span></span>|<span data-ttu-id="b223d-109">`Reset` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b223d-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="b223d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b223d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b223d-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b223d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b223d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b223d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b223d-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b223d-113">The call timed out.</span></span>|  
|<span data-ttu-id="b223d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b223d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b223d-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b223d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b223d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b223d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b223d-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b223d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b223d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b223d-118">E_FAIL</span></span>|<span data-ttu-id="b223d-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b223d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b223d-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b223d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b223d-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b223d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b223d-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b223d-122">Requirements</span></span>  
 <span data-ttu-id="b223d-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b223d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b223d-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b223d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b223d-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b223d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b223d-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b223d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b223d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b223d-127">See also</span></span>

- [<span data-ttu-id="b223d-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b223d-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b223d-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b223d-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b223d-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b223d-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="b223d-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="b223d-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b223d-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b223d-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
