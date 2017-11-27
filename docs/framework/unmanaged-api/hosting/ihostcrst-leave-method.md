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
ms.openlocfilehash: 21e9a99e4fd22b2cc7d954d0f7316c45ffd7074c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="b486f-102">IHostCrst::Leave — Metoda</span><span class="sxs-lookup"><span data-stu-id="b486f-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="b486f-103">Pozostawia sekcja krytyczna, reprezentowanego przez bieżące wystąpienie klasy [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b486f-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b486f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b486f-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b486f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b486f-105">Return Value</span></span>  
  
|<span data-ttu-id="b486f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b486f-106">HRESULT</span></span>|<span data-ttu-id="b486f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b486f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b486f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b486f-108">S_OK</span></span>|<span data-ttu-id="b486f-109">`Leave`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b486f-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="b486f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b486f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b486f-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b486f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b486f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b486f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b486f-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b486f-113">The call timed out.</span></span>|  
|<span data-ttu-id="b486f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b486f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b486f-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b486f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b486f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b486f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b486f-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b486f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b486f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b486f-118">E_FAIL</span></span>|<span data-ttu-id="b486f-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b486f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b486f-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b486f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b486f-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b486f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b486f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b486f-122">Remarks</span></span>  
 <span data-ttu-id="b486f-123">`Leave`Umożliwia środowisko CLR, które komunikują się bezpośrednio z hosta wątkowość implementacji, a nie przy użyciu odpowiedniego Win32 `LeaveCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b486f-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="b486f-124">Wątku, który przejmuje sekcja krytyczna reprezentowany przez bieżący `IHostCrst` należy wywołać metodę wystąpienia `Leave` po za każdym razem, wejdzie ona tej sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="b486f-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b486f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b486f-125">Requirements</span></span>  
 <span data-ttu-id="b486f-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b486f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b486f-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b486f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b486f-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b486f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b486f-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b486f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b486f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b486f-130">See Also</span></span>  
 [<span data-ttu-id="b486f-131">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="b486f-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b486f-132">IHostCrst — interfejs</span><span class="sxs-lookup"><span data-stu-id="b486f-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="b486f-133">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="b486f-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
