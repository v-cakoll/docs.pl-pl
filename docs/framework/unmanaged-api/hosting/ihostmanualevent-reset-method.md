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
ms.openlocfilehash: 464093291648d7c5c1f2001fbaef85fcd5d592de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136802"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="e1623-102">IHostManualEvent::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1623-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="e1623-103">Resetuje bieżące wystąpienie [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) do stanu niesygnalizującego.</span><span class="sxs-lookup"><span data-stu-id="e1623-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1623-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1623-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e1623-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e1623-105">Return Value</span></span>  
  
|<span data-ttu-id="e1623-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1623-106">HRESULT</span></span>|<span data-ttu-id="e1623-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e1623-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1623-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1623-108">S_OK</span></span>|<span data-ttu-id="e1623-109">`Reset` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e1623-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="e1623-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1623-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1623-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1623-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1623-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1623-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1623-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e1623-113">The call timed out.</span></span>|  
|<span data-ttu-id="e1623-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1623-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1623-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e1623-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1623-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1623-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1623-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e1623-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1623-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1623-118">E_FAIL</span></span>|<span data-ttu-id="e1623-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1623-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1623-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="e1623-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1623-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e1623-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1623-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1623-122">Requirements</span></span>  
 <span data-ttu-id="e1623-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1623-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1623-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e1623-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1623-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1623-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1623-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1623-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1623-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1623-127">See also</span></span>

- [<span data-ttu-id="e1623-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1623-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e1623-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1623-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e1623-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1623-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e1623-131">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1623-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="e1623-132">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1623-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
