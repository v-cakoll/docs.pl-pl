---
title: "IHostCrst::Leave — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.Leave
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 391aff3920e7ea2ef010ce7d97bdedb4e636dc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="87287-102">IHostCrst::Leave — Metoda</span><span class="sxs-lookup"><span data-stu-id="87287-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="87287-103">Pozostawia sekcja krytyczna, reprezentowanego przez bieżące wystąpienie klasy [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="87287-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87287-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87287-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="87287-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87287-105">Return Value</span></span>  
  
|<span data-ttu-id="87287-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87287-106">HRESULT</span></span>|<span data-ttu-id="87287-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87287-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87287-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="87287-108">S_OK</span></span>|<span data-ttu-id="87287-109">`Leave`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87287-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="87287-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87287-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87287-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="87287-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87287-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87287-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87287-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="87287-113">The call timed out.</span></span>|  
|<span data-ttu-id="87287-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87287-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87287-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="87287-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87287-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87287-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87287-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="87287-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87287-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87287-118">E_FAIL</span></span>|<span data-ttu-id="87287-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="87287-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87287-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="87287-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87287-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="87287-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87287-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87287-122">Remarks</span></span>  
 <span data-ttu-id="87287-123">`Leave`Umożliwia środowisko CLR, które komunikują się bezpośrednio z hosta wątkowość implementacji, a nie przy użyciu odpowiedniego Win32 `LeaveCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="87287-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="87287-124">Wątku, który przejmuje sekcja krytyczna reprezentowany przez bieżący `IHostCrst` należy wywołać metodę wystąpienia `Leave` po za każdym razem, wejdzie ona tej sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="87287-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87287-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87287-125">Requirements</span></span>  
 <span data-ttu-id="87287-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87287-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87287-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87287-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87287-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87287-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87287-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87287-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87287-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87287-130">See Also</span></span>  
 [<span data-ttu-id="87287-131">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87287-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="87287-132">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="87287-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="87287-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87287-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
