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
ms.openlocfilehash: 1114fc744ac1811585f2c5a94858b75eda00815c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136756"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="92b61-102">IHostManualEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="92b61-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="92b61-103">Ustawia bieżące wystąpienie [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) na sygnał.</span><span class="sxs-lookup"><span data-stu-id="92b61-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92b61-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="92b61-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92b61-105">Return Value</span></span>  
  
|<span data-ttu-id="92b61-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92b61-106">HRESULT</span></span>|<span data-ttu-id="92b61-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92b61-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92b61-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="92b61-108">S_OK</span></span>|<span data-ttu-id="92b61-109">`Set` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="92b61-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="92b61-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92b61-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92b61-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="92b61-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92b61-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92b61-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92b61-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="92b61-113">The call timed out.</span></span>|  
|<span data-ttu-id="92b61-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92b61-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92b61-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="92b61-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92b61-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92b61-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92b61-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="92b61-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92b61-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92b61-118">E_FAIL</span></span>|<span data-ttu-id="92b61-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="92b61-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92b61-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="92b61-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92b61-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92b61-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92b61-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92b61-122">Requirements</span></span>  
 <span data-ttu-id="92b61-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b61-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b61-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92b61-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92b61-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92b61-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92b61-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b61-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b61-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92b61-127">See also</span></span>

- [<span data-ttu-id="92b61-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b61-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="92b61-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b61-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="92b61-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b61-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="92b61-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b61-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="92b61-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b61-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
