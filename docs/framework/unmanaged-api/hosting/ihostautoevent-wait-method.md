---
title: IHostAutoEvent::Wait — Metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b07b3649cc1d7fcc2c75cbbd59414ee67819103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217929"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="838fb-102">IHostAutoEvent::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="838fb-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="838fb-103">Powoduje, że bieżący [ihostautoevent —](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienie do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="838fb-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="838fb-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="838fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="838fb-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="838fb-106">[in] Liczba milisekund bieżącego `IHostAutoEvent` wystąpienia powinien odczekać przez zwracać, jeśli żaden wątek lub włókna przejmuje na własność.</span><span class="sxs-lookup"><span data-stu-id="838fb-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="838fb-107">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości określające akcję host powinien wykonać, jeśli operacja bloków.</span><span class="sxs-lookup"><span data-stu-id="838fb-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="838fb-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="838fb-108">Return Value</span></span>  
  
|<span data-ttu-id="838fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="838fb-109">HRESULT</span></span>|<span data-ttu-id="838fb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="838fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="838fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="838fb-111">S_OK</span></span>|`Wait` <span data-ttu-id="838fb-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="838fb-112">returned successfully.</span></span>|  
|<span data-ttu-id="838fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="838fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="838fb-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="838fb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="838fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="838fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="838fb-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="838fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="838fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="838fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="838fb-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="838fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="838fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="838fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="838fb-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="838fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="838fb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="838fb-121">E_FAIL</span></span>|<span data-ttu-id="838fb-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="838fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="838fb-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="838fb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="838fb-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="838fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="838fb-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="838fb-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="838fb-126">Host wykrył zakleszczenie w przedziale czasu oczekiwania i wybrać zdarzenie, reprezentowane przez bieżącą `IHostAutoEvent` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="838fb-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="838fb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="838fb-127">Requirements</span></span>  
 <span data-ttu-id="838fb-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838fb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838fb-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="838fb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="838fb-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="838fb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="838fb-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="838fb-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="838fb-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="838fb-132">See also</span></span>

- [<span data-ttu-id="838fb-133">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="838fb-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="838fb-134">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="838fb-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="838fb-135">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="838fb-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="838fb-136">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="838fb-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
