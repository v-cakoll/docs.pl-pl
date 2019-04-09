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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148567"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="3bc22-102">IHostManualEvent::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bc22-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="3bc22-103">Przywraca bieżące [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="3bc22-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc22-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3bc22-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3bc22-105">Return Value</span></span>  
  
|<span data-ttu-id="3bc22-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bc22-106">HRESULT</span></span>|<span data-ttu-id="3bc22-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc22-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bc22-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bc22-108">S_OK</span></span>|`Reset` <span data-ttu-id="3bc22-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="3bc22-109">returned successfully.</span></span>|  
|<span data-ttu-id="3bc22-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bc22-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bc22-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3bc22-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bc22-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bc22-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bc22-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3bc22-113">The call timed out.</span></span>|  
|<span data-ttu-id="3bc22-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bc22-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bc22-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="3bc22-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bc22-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bc22-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bc22-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3bc22-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bc22-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bc22-118">E_FAIL</span></span>|<span data-ttu-id="3bc22-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3bc22-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bc22-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3bc22-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bc22-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3bc22-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bc22-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bc22-122">Requirements</span></span>  
 <span data-ttu-id="3bc22-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bc22-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bc22-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bc22-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bc22-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bc22-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3bc22-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3bc22-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bc22-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bc22-127">See also</span></span>

- [<span data-ttu-id="3bc22-128">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bc22-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3bc22-129">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bc22-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3bc22-130">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bc22-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3bc22-131">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bc22-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="3bc22-132">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bc22-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
