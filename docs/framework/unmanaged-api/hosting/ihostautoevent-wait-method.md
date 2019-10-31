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
ms.openlocfilehash: 0258999bae8b04ddaccf264276d1439b027b4a43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195887"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="91882-102">IHostAutoEvent::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="91882-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="91882-103">Powoduje, że bieżące wystąpienie [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) zaczeka, aż jego właścicielem lub upłynie określony czas.</span><span class="sxs-lookup"><span data-stu-id="91882-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91882-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91882-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91882-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="91882-106">podczas Liczba milisekund, przez jaką bieżące wystąpienie `IHostAutoEvent` powinno czekać przed zwróceniem, jeśli żaden wątek ani włókna nie przejmią własności.</span><span class="sxs-lookup"><span data-stu-id="91882-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="91882-107">podczas Jedna z wartości [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , określająca akcję, którą powinien wykonać host w przypadku tej operacji.</span><span class="sxs-lookup"><span data-stu-id="91882-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91882-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91882-108">Return Value</span></span>  
  
|<span data-ttu-id="91882-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91882-109">HRESULT</span></span>|<span data-ttu-id="91882-110">Opis</span><span class="sxs-lookup"><span data-stu-id="91882-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91882-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91882-111">S_OK</span></span>|<span data-ttu-id="91882-112">`Wait` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="91882-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="91882-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91882-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91882-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="91882-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91882-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91882-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91882-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="91882-116">The call timed out.</span></span>|  
|<span data-ttu-id="91882-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91882-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91882-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="91882-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91882-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91882-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91882-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="91882-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91882-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91882-121">E_FAIL</span></span>|<span data-ttu-id="91882-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="91882-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91882-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="91882-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91882-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91882-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91882-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="91882-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="91882-126">Host wykrył zakleszczenie w interwale oczekiwania i wybiera zdarzenie reprezentowane przez bieżące wystąpienie `IHostAutoEvent` jako ofiarę zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="91882-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91882-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91882-127">Requirements</span></span>  
 <span data-ttu-id="91882-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91882-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91882-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91882-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91882-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91882-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91882-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91882-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91882-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91882-132">See also</span></span>

- [<span data-ttu-id="91882-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="91882-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="91882-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="91882-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="91882-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="91882-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="91882-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="91882-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
