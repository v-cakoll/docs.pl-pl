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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599419"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="ea78f-102">IHostAutoEvent::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea78f-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="ea78f-103">Powoduje, że bieżący [ihostautoevent —](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienie do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="ea78f-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea78f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea78f-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea78f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea78f-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="ea78f-106">[in] Liczba milisekund bieżącego `IHostAutoEvent` wystąpienia powinien odczekać przez zwracać, jeśli żaden wątek lub włókna przejmuje na własność.</span><span class="sxs-lookup"><span data-stu-id="ea78f-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="ea78f-107">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości określające akcję host powinien wykonać, jeśli operacja bloków.</span><span class="sxs-lookup"><span data-stu-id="ea78f-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea78f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ea78f-108">Return Value</span></span>  
  
|<span data-ttu-id="ea78f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea78f-109">HRESULT</span></span>|<span data-ttu-id="ea78f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ea78f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea78f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea78f-111">S_OK</span></span>|<span data-ttu-id="ea78f-112">`Wait` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ea78f-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="ea78f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea78f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea78f-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ea78f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea78f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea78f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea78f-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ea78f-116">The call timed out.</span></span>|  
|<span data-ttu-id="ea78f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea78f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea78f-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ea78f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea78f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea78f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea78f-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ea78f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea78f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea78f-121">E_FAIL</span></span>|<span data-ttu-id="ea78f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ea78f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea78f-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ea78f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea78f-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea78f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ea78f-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="ea78f-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="ea78f-126">Host wykrył zakleszczenie w przedziale czasu oczekiwania i wybrać zdarzenie, reprezentowane przez bieżącą `IHostAutoEvent` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="ea78f-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea78f-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea78f-127">Requirements</span></span>  
 <span data-ttu-id="ea78f-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea78f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea78f-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea78f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea78f-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea78f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea78f-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea78f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea78f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea78f-132">See also</span></span>

- [<span data-ttu-id="ea78f-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea78f-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ea78f-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea78f-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ea78f-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea78f-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="ea78f-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea78f-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
