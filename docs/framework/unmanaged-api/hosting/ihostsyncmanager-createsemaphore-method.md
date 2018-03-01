---
title: "IHostSyncManager::CreateSemaphore — Metoda"
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
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8df29b3eeb565aaa4a977762fcc453fb985e40d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="6b8a7-102">IHostSyncManager::CreateSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b8a7-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="6b8a7-103">Tworzy [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) obiektu dla środowisko uruchomieniowe języka wspólnego (CLR) ma być używana jako semafor Czekaj zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b8a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b8a7-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b8a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b8a7-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="6b8a7-106">[in] Liczba początkowa `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="6b8a7-107">[in] Maksymalna liczba dla `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="6b8a7-108">[out] Wskaźnik do adresu `IHostSemaphore` wystąpienia, lub wartość null, jeśli nie można utworzyć semafora.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b8a7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b8a7-109">Return Value</span></span>  
  
|<span data-ttu-id="6b8a7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b8a7-110">HRESULT</span></span>|<span data-ttu-id="6b8a7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6b8a7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b8a7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b8a7-112">S_OK</span></span>|<span data-ttu-id="6b8a7-113">`CreateSemaphore`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="6b8a7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b8a7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b8a7-115">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b8a7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b8a7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b8a7-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-117">The call timed out.</span></span>|  
|<span data-ttu-id="6b8a7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b8a7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b8a7-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b8a7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b8a7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b8a7-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b8a7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b8a7-122">E_FAIL</span></span>|<span data-ttu-id="6b8a7-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b8a7-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b8a7-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b8a7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6b8a7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6b8a7-127">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b8a7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b8a7-128">Remarks</span></span>  
 <span data-ttu-id="6b8a7-129">`CreateSemaphore`odzwierciedla funkcji Win32, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="6b8a7-130">`dwInitial` i `dwMax` parametry korzysta z tej samej semantyki Licznik semafora jako Win32 `lInitialCount` i `lMaximumCount` parametry, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="6b8a7-131">`dwInitial`musi należeć do zakresu od zera i `dwMax`włącznie.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="6b8a7-132">`dwMax`musi być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="6b8a7-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b8a7-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b8a7-133">Requirements</span></span>  
 <span data-ttu-id="6b8a7-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b8a7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b8a7-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b8a7-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b8a7-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b8a7-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b8a7-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b8a7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b8a7-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b8a7-138">See Also</span></span>  
 [<span data-ttu-id="6b8a7-139">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b8a7-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6b8a7-140">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b8a7-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="6b8a7-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b8a7-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
