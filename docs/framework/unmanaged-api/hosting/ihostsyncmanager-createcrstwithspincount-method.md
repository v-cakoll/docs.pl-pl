---
title: "IHostSyncManager::CreateCrstWithSpinCount — Metoda"
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
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31830f97cff1c302ee573b8248eb1d83e696ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="e2928-102">IHostSyncManager::CreateCrstWithSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2928-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="e2928-103">Tworzy obiekt sekcja krytyczna z licznikiem pokrętła do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="e2928-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2928-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2928-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2928-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2928-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="e2928-106">[in] Określa liczbę pokrętła dla obiekt sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="e2928-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="e2928-107">[out] Wskaźnik do adresu [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="e2928-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2928-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e2928-108">Return Value</span></span>  
  
|<span data-ttu-id="e2928-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2928-109">HRESULT</span></span>|<span data-ttu-id="e2928-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e2928-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2928-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2928-111">S_OK</span></span>|<span data-ttu-id="e2928-112">`CreateCrstWithSpinCount`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e2928-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="e2928-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2928-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2928-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e2928-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e2928-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2928-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2928-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e2928-116">The call timed out.</span></span>|  
|<span data-ttu-id="e2928-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2928-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2928-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e2928-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2928-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2928-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2928-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e2928-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2928-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2928-121">E_FAIL</span></span>|<span data-ttu-id="e2928-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e2928-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2928-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e2928-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2928-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e2928-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e2928-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e2928-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e2928-126">Za mało pamięci nie była dostępna, można utworzyć żądanego sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="e2928-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2928-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2928-127">Remarks</span></span>  
 <span data-ttu-id="e2928-128">Liczba pokrętła jest używana tylko w systemie wieloprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="e2928-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="e2928-129">Liczba pokrętła określa liczbę powtórzeń wątek wywołujący musi pokrętła przed przesłaniem operację oczekiwania na semafora skojarzony z sekcji krytycznej niedostępny.</span><span class="sxs-lookup"><span data-stu-id="e2928-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="e2928-130">Jeśli sekcja krytyczna staje się wolnego podczas operacji pokrętła, wątek wywołujący pozwala uniknąć operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e2928-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="e2928-131">`CreateCrstWithSpinCount`odzwierciedla Win32 `InitializeCriticalSectionAndSpinCount` funkcji.</span><span class="sxs-lookup"><span data-stu-id="e2928-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2928-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2928-132">Requirements</span></span>  
 <span data-ttu-id="e2928-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2928-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2928-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2928-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2928-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2928-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2928-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2928-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2928-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2928-137">See Also</span></span>  
 [<span data-ttu-id="e2928-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2928-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e2928-139">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2928-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="e2928-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2928-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
