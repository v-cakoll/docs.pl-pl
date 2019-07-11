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
ms.openlocfilehash: 37ba54665dbd8d10c7e7aac9a0692c8882fb5209
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767289"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="10738-102">IHostManualEvent::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="10738-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="10738-103">Przywraca bieżące [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="10738-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10738-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10738-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="10738-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="10738-105">Return Value</span></span>  
  
|<span data-ttu-id="10738-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10738-106">HRESULT</span></span>|<span data-ttu-id="10738-107">Opis</span><span class="sxs-lookup"><span data-stu-id="10738-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10738-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="10738-108">S_OK</span></span>|<span data-ttu-id="10738-109">`Reset` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="10738-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="10738-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10738-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10738-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="10738-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10738-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10738-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10738-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="10738-113">The call timed out.</span></span>|  
|<span data-ttu-id="10738-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10738-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10738-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="10738-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10738-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10738-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10738-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="10738-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10738-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10738-118">E_FAIL</span></span>|<span data-ttu-id="10738-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="10738-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10738-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="10738-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10738-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10738-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10738-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10738-122">Requirements</span></span>  
 <span data-ttu-id="10738-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10738-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10738-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10738-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10738-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10738-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10738-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10738-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10738-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10738-127">See also</span></span>

- [<span data-ttu-id="10738-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="10738-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="10738-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="10738-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="10738-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="10738-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="10738-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="10738-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="10738-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="10738-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
