---
title: IHostSyncManager::SetCLRSyncManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27cf1ab377a3bb51700b287024d801e75107c8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464924"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="cfb51-102">IHostSyncManager::SetCLRSyncManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfb51-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="cfb51-103">Zestawy [iclrsyncmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) wystąpienia do skojarzenia z bieżącego [ihostsyncmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cfb51-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfb51-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfb51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfb51-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="cfb51-106">[in] Wskaźnik do `ICLRSyncManager` wystąpienia dostarczane przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cfb51-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfb51-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cfb51-107">Return Value</span></span>  
  
|<span data-ttu-id="cfb51-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfb51-108">HRESULT</span></span>|<span data-ttu-id="cfb51-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cfb51-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfb51-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfb51-110">S_OK</span></span>|<span data-ttu-id="cfb51-111">`SetCLRSyncManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cfb51-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="cfb51-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cfb51-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cfb51-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cfb51-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cfb51-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cfb51-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cfb51-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cfb51-115">The call timed out.</span></span>|  
|<span data-ttu-id="cfb51-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cfb51-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cfb51-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cfb51-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cfb51-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cfb51-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cfb51-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cfb51-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cfb51-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfb51-120">E_FAIL</span></span>|<span data-ttu-id="cfb51-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cfb51-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cfb51-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cfb51-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cfb51-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cfb51-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfb51-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfb51-124">Remarks</span></span>  
 <span data-ttu-id="cfb51-125">W celu ułatwienia komunikacji między hostem a środowisko CLR, interfejsami hostingu są ogólnie dostępne w pary.</span><span class="sxs-lookup"><span data-stu-id="cfb51-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="cfb51-126">Jednego członka pary jest implementowany przez hosta i innego członka jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="cfb51-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="cfb51-127">Jako wdrażania po stronie hosta `IHostSyncManager` interfejsu odnosi się do `ICLRSyncManager` interfejs implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="cfb51-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="cfb51-128">CLR wywołuje `SetCLRSyncManager` umożliwiają określanie wartości `ICLRSyncManager` wystąpienia hosta do skojarzenia z bieżącego `IHostSyncManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cfb51-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb51-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfb51-129">Requirements</span></span>  
 <span data-ttu-id="cfb51-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb51-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb51-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfb51-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfb51-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfb51-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfb51-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb51-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb51-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfb51-134">See also</span></span>
- [<span data-ttu-id="cfb51-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfb51-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="cfb51-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfb51-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
