---
title: "IHostManualEvent::Reset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1bbd10437662fc8b7fbb52d65d196d7a519538b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="73e5f-102">IHostManualEvent::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="73e5f-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="73e5f-103">Przywraca bieżące [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia-sygnalizowane stan.</span><span class="sxs-lookup"><span data-stu-id="73e5f-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73e5f-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="73e5f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73e5f-105">Return Value</span></span>  
  
|<span data-ttu-id="73e5f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73e5f-106">HRESULT</span></span>|<span data-ttu-id="73e5f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="73e5f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73e5f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="73e5f-108">S_OK</span></span>|<span data-ttu-id="73e5f-109">`Reset`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="73e5f-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="73e5f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73e5f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73e5f-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="73e5f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="73e5f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73e5f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73e5f-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="73e5f-113">The call timed out.</span></span>|  
|<span data-ttu-id="73e5f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73e5f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73e5f-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="73e5f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73e5f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73e5f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73e5f-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="73e5f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73e5f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73e5f-118">E_FAIL</span></span>|<span data-ttu-id="73e5f-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="73e5f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73e5f-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="73e5f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73e5f-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="73e5f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73e5f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73e5f-122">Requirements</span></span>  
 <span data-ttu-id="73e5f-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e5f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e5f-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73e5f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73e5f-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73e5f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73e5f-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e5f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e5f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73e5f-127">See Also</span></span>  
 [<span data-ttu-id="73e5f-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e5f-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="73e5f-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e5f-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="73e5f-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e5f-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="73e5f-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e5f-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="73e5f-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e5f-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
