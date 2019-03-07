---
title: IHostSyncManager::CreateCrstWithSpinCount — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4dd73efbad5ffac47c8585facd1717d77147fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501591"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="49abc-102">IHostSyncManager::CreateCrstWithSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="49abc-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="49abc-103">Tworzy obiekt sekcję krytyczną z liczbą pokrętła do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="49abc-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49abc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49abc-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49abc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49abc-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="49abc-106">[in] Określa liczbę pokrętła dla obiektu sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="49abc-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="49abc-107">[out] Wskaźnik na adres [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="49abc-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49abc-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49abc-108">Return Value</span></span>  
  
|<span data-ttu-id="49abc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49abc-109">HRESULT</span></span>|<span data-ttu-id="49abc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="49abc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49abc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="49abc-111">S_OK</span></span>|<span data-ttu-id="49abc-112">`CreateCrstWithSpinCount` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="49abc-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="49abc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49abc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49abc-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="49abc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49abc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49abc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49abc-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="49abc-116">The call timed out.</span></span>|  
|<span data-ttu-id="49abc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49abc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49abc-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="49abc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49abc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49abc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49abc-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="49abc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49abc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49abc-121">E_FAIL</span></span>|<span data-ttu-id="49abc-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="49abc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49abc-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="49abc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49abc-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49abc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49abc-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="49abc-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="49abc-126">Nie ma wystarczającej ilości dostępnej pamięci na utworzyć żądany sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="49abc-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49abc-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49abc-127">Remarks</span></span>  
 <span data-ttu-id="49abc-128">Liczba pokrętła jest używana tylko w systemie wieloprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="49abc-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="49abc-129">Liczba pokrętła określa liczbę przypadków, gdy wątek wywołujący musi pokrętła, przed wykonaniem operacji oczekiwania na semafor, który jest skojarzony z niedostępny sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="49abc-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="49abc-130">Jeśli podczas operacji pokrętła zwolniony sekcję krytyczną, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="49abc-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="49abc-131">`CreateCrstWithSpinCount` odzwierciedla Win32 `InitializeCriticalSectionAndSpinCount` funkcji.</span><span class="sxs-lookup"><span data-stu-id="49abc-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49abc-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49abc-132">Requirements</span></span>  
 <span data-ttu-id="49abc-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49abc-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49abc-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="49abc-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49abc-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49abc-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49abc-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49abc-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49abc-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49abc-137">See also</span></span>
- [<span data-ttu-id="49abc-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="49abc-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="49abc-139">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="49abc-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="49abc-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="49abc-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
