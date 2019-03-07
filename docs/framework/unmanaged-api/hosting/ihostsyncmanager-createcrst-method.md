---
title: IHostSyncManager::CreateCrst — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a44e85d0f697b8388b45373340e1691892ea499
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503271"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="0acb3-102">IHostSyncManager::CreateCrst — Metoda</span><span class="sxs-lookup"><span data-stu-id="0acb3-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="0acb3-103">Tworzy obiekt sekcję krytyczną synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="0acb3-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0acb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0acb3-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0acb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0acb3-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="0acb3-106">[out] Wskaźnik na adres [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia implementowane przez hosta lub wartość null, jeśli nie można utworzyć sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="0acb3-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0acb3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0acb3-107">Return Value</span></span>  
  
|<span data-ttu-id="0acb3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0acb3-108">HRESULT</span></span>|<span data-ttu-id="0acb3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0acb3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0acb3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0acb3-110">S_OK</span></span>|<span data-ttu-id="0acb3-111">`CreateCrst` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0acb3-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="0acb3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0acb3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0acb3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0acb3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0acb3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0acb3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0acb3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0acb3-115">The call timed out.</span></span>|  
|<span data-ttu-id="0acb3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0acb3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0acb3-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="0acb3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0acb3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0acb3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0acb3-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0acb3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0acb3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0acb3-120">E_FAIL</span></span>|<span data-ttu-id="0acb3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0acb3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0acb3-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0acb3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0acb3-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0acb3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0acb3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0acb3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0acb3-125">Nie ma wystarczającej ilości dostępnej pamięci na utworzyć żądany sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="0acb3-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0acb3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0acb3-126">Remarks</span></span>  
 <span data-ttu-id="0acb3-127">Obiekty sekcję krytyczną zapewniają podobne do dostarczony przez obiekt mutex synchronizacji z tą różnicą, że sekcje krytyczne mogą korzystać tylko wątki pojedynczego procesu.</span><span class="sxs-lookup"><span data-stu-id="0acb3-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="0acb3-128">`CreateCrst` odzwierciedla Win32 `InitializeCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0acb3-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0acb3-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0acb3-129">Requirements</span></span>  
 <span data-ttu-id="0acb3-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0acb3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0acb3-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0acb3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0acb3-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0acb3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0acb3-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0acb3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acb3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0acb3-134">See also</span></span>
- [<span data-ttu-id="0acb3-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0acb3-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0acb3-136">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="0acb3-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="0acb3-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0acb3-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="0acb3-138">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="0acb3-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="0acb3-139">Muteksy</span><span class="sxs-lookup"><span data-stu-id="0acb3-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)
- [<span data-ttu-id="0acb3-140">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="0acb3-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
