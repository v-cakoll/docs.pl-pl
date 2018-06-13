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
ms.openlocfilehash: 7921f0361d7369cddf14dd1ab477529d1bbac481
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439364"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="a75cc-102">IHostAutoEvent::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="a75cc-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="a75cc-103">Powoduje, że bieżący [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia poczekać, aż należy on do lub z określoną ilością pamięci upłynie czas.</span><span class="sxs-lookup"><span data-stu-id="a75cc-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a75cc-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a75cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a75cc-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="a75cc-106">[in] Wyrażony w milisekundach czas bieżący `IHostAutoEvent` wystąpienia powinien zaczekać na zwrócenie, jeśli żadnego wątku lub włókna przejmuje.</span><span class="sxs-lookup"><span data-stu-id="a75cc-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="a75cc-107">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości określające akcję hosta powinien wykonać, jeśli ta operacja bloków.</span><span class="sxs-lookup"><span data-stu-id="a75cc-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a75cc-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a75cc-108">Return Value</span></span>  
  
|<span data-ttu-id="a75cc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a75cc-109">HRESULT</span></span>|<span data-ttu-id="a75cc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a75cc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a75cc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a75cc-111">S_OK</span></span>|<span data-ttu-id="a75cc-112">`Wait` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a75cc-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="a75cc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a75cc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a75cc-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a75cc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a75cc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a75cc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a75cc-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a75cc-116">The call timed out.</span></span>|  
|<span data-ttu-id="a75cc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a75cc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a75cc-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a75cc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a75cc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a75cc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a75cc-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a75cc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a75cc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a75cc-121">E_FAIL</span></span>|<span data-ttu-id="a75cc-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a75cc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a75cc-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a75cc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a75cc-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a75cc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a75cc-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="a75cc-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="a75cc-126">Host wykrył zakleszczenie w interwale oczekiwania, a wybrano zdarzeń reprezentowany przez bieżący `IHostAutoEvent` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a75cc-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a75cc-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a75cc-127">Requirements</span></span>  
 <span data-ttu-id="a75cc-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75cc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75cc-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a75cc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a75cc-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a75cc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a75cc-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75cc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75cc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a75cc-132">See Also</span></span>  
 [<span data-ttu-id="a75cc-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a75cc-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a75cc-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a75cc-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="a75cc-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a75cc-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="a75cc-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a75cc-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
