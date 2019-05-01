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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d60cdee0a5357f7e117dc902b073049f3bbaea9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984389"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="276b9-102">IHostCrst::Leave — Metoda</span><span class="sxs-lookup"><span data-stu-id="276b9-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="276b9-103">Pozostawia sekcję krytyczną, która jest reprezentowana przez bieżące wystąpienie [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="276b9-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="276b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="276b9-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="276b9-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="276b9-105">Return Value</span></span>  
  
|<span data-ttu-id="276b9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="276b9-106">HRESULT</span></span>|<span data-ttu-id="276b9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="276b9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="276b9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="276b9-108">S_OK</span></span>|<span data-ttu-id="276b9-109">`Leave` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="276b9-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="276b9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="276b9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="276b9-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="276b9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="276b9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="276b9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="276b9-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="276b9-113">The call timed out.</span></span>|  
|<span data-ttu-id="276b9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="276b9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="276b9-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="276b9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="276b9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="276b9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="276b9-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="276b9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="276b9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="276b9-118">E_FAIL</span></span>|<span data-ttu-id="276b9-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="276b9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="276b9-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="276b9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="276b9-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="276b9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="276b9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="276b9-122">Remarks</span></span>  
 <span data-ttu-id="276b9-123">`Leave` Umożliwia środowisku CLR komunikują się bezpośrednio z hosta wątkowości wdrożenia, a nie przy użyciu odpowiedniego Win32 `LeaveCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="276b9-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="276b9-124">Wątek, który przejmuje na własność sekcję krytyczną, reprezentowane przez bieżącą `IHostCrst` należy wywołać wystąpienie `Leave` po każdym wchodzi tę sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="276b9-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="276b9-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="276b9-125">Requirements</span></span>  
 <span data-ttu-id="276b9-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="276b9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="276b9-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="276b9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="276b9-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="276b9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="276b9-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="276b9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276b9-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="276b9-130">See also</span></span>

- [<span data-ttu-id="276b9-131">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="276b9-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="276b9-132">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="276b9-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="276b9-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="276b9-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
