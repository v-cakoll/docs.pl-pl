---
title: IHostCrst::Leave — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: 050af068579d84b984ed83377d0c201e281bd154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130532"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="a9713-102">IHostCrst::Leave — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9713-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="a9713-103">Pozostawia sekcję krytyczną, która jest reprezentowana przez bieżące wystąpienie elementu [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a9713-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9713-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9713-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a9713-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9713-105">Return Value</span></span>  
  
|<span data-ttu-id="a9713-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9713-106">HRESULT</span></span>|<span data-ttu-id="a9713-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a9713-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9713-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9713-108">S_OK</span></span>|<span data-ttu-id="a9713-109">`Leave` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a9713-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="a9713-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9713-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9713-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a9713-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9713-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9713-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9713-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a9713-113">The call timed out.</span></span>|  
|<span data-ttu-id="a9713-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9713-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9713-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a9713-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9713-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9713-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9713-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a9713-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9713-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9713-118">E_FAIL</span></span>|<span data-ttu-id="a9713-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a9713-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9713-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a9713-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9713-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9713-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9713-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9713-122">Remarks</span></span>  
 <span data-ttu-id="a9713-123">`Leave` pozwala środowisko CLR komunikować się bezpośrednio z implementacją wątkowości hosta, a nie przy użyciu odpowiedniej funkcji `LeaveCriticalSection` Win32.</span><span class="sxs-lookup"><span data-stu-id="a9713-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="a9713-124">Wątek, który przejmuje własność sekcji krytycznej reprezentowanej przez bieżące wystąpienie `IHostCrst`, musi wywołać `Leave` raz dla każdej operacji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="a9713-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9713-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9713-125">Requirements</span></span>  
 <span data-ttu-id="a9713-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9713-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9713-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9713-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9713-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9713-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9713-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9713-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9713-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9713-130">See also</span></span>

- [<span data-ttu-id="a9713-131">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9713-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a9713-132">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9713-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="a9713-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9713-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
