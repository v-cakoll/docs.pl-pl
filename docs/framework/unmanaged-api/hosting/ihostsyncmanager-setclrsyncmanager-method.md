---
title: "IHostSyncManager::SetCLRSyncManager — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.SetCLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca59f0d2617c6fb244b2b1ed7b5cf46a7d5869f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="e0c88-102">IHostSyncManager::SetCLRSyncManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0c88-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="e0c88-103">Ustawia [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) wystąpienie do skojarzenia z bieżącym [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e0c88-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0c88-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0c88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0c88-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="e0c88-106">[in] Wskaźnik do `ICLRSyncManager` wystąpienia dostarczony przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e0c88-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0c88-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0c88-107">Return Value</span></span>  
  
|<span data-ttu-id="e0c88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0c88-108">HRESULT</span></span>|<span data-ttu-id="e0c88-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e0c88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0c88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0c88-110">S_OK</span></span>|<span data-ttu-id="e0c88-111">`SetCLRSyncManager`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e0c88-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="e0c88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0c88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0c88-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e0c88-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0c88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0c88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0c88-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e0c88-115">The call timed out.</span></span>|  
|<span data-ttu-id="e0c88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0c88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0c88-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e0c88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0c88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0c88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0c88-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e0c88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0c88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0c88-120">E_FAIL</span></span>|<span data-ttu-id="e0c88-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e0c88-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0c88-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e0c88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0c88-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0c88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0c88-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0c88-124">Remarks</span></span>  
 <span data-ttu-id="e0c88-125">W celu ułatwienia komunikacji między hostem a CLR, interfejsy hostingu zazwyczaj dostępne w pary.</span><span class="sxs-lookup"><span data-stu-id="e0c88-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="e0c88-126">Jeden element członkowski pary jest implementowany przez hosta i innego członka jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e0c88-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="e0c88-127">Jako implementacja po stronie hosta `IHostSyncManager` interfejsu odpowiada `ICLRSyncManager` interfejsu zaimplementowanego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e0c88-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="e0c88-128">Wywołania CLR `SetCLRSyncManager` podać `ICLRSyncManager` wystąpienia hosta do skojarzenia z bieżącym `IHostSyncManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e0c88-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c88-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0c88-129">Requirements</span></span>  
 <span data-ttu-id="e0c88-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0c88-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c88-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0c88-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0c88-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0c88-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0c88-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c88-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c88-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0c88-134">See Also</span></span>  
 [<span data-ttu-id="e0c88-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0c88-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e0c88-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0c88-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
