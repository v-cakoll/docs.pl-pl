---
title: "IHostManualEvent::Set — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30dcb7232d6e0f7d42de48fefd2fbb9433a50405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="dbed2-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="dbed2-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="dbed2-103">Ustawia bieżący [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia sygnałowego stanu.</span><span class="sxs-lookup"><span data-stu-id="dbed2-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbed2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbed2-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dbed2-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dbed2-105">Return Value</span></span>  
  
|<span data-ttu-id="dbed2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbed2-106">HRESULT</span></span>|<span data-ttu-id="dbed2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dbed2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbed2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbed2-108">S_OK</span></span>|<span data-ttu-id="dbed2-109">`Set`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dbed2-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="dbed2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbed2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbed2-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbed2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbed2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbed2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbed2-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbed2-113">The call timed out.</span></span>|  
|<span data-ttu-id="dbed2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbed2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbed2-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dbed2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbed2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbed2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbed2-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dbed2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbed2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbed2-118">E_FAIL</span></span>|<span data-ttu-id="dbed2-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dbed2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbed2-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dbed2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbed2-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbed2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbed2-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbed2-122">Requirements</span></span>  
 <span data-ttu-id="dbed2-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbed2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbed2-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbed2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbed2-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbed2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbed2-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbed2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbed2-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbed2-127">See Also</span></span>  
 [<span data-ttu-id="dbed2-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbed2-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dbed2-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbed2-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="dbed2-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbed2-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="dbed2-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbed2-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="dbed2-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbed2-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
