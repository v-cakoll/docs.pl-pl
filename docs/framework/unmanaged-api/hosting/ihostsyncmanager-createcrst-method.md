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
ms.openlocfilehash: 8b63b283a28ed27a70698c45bdc87d63fef0daf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117952"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="f5683-102">IHostSyncManager::CreateCrst — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5683-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="f5683-103">Tworzy obiekt sekcję krytyczną synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="f5683-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5683-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5683-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5683-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5683-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="f5683-106">[out] Wskaźnik na adres [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia implementowane przez hosta lub wartość null, jeśli nie można utworzyć sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="f5683-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5683-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5683-107">Return Value</span></span>  
  
|<span data-ttu-id="f5683-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5683-108">HRESULT</span></span>|<span data-ttu-id="f5683-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f5683-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5683-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5683-110">S_OK</span></span>|`CreateCrst` <span data-ttu-id="f5683-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f5683-111">returned successfully.</span></span>|  
|<span data-ttu-id="f5683-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5683-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5683-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f5683-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5683-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5683-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5683-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f5683-115">The call timed out.</span></span>|  
|<span data-ttu-id="f5683-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5683-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5683-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="f5683-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5683-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5683-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5683-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f5683-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5683-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5683-120">E_FAIL</span></span>|<span data-ttu-id="f5683-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f5683-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5683-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f5683-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5683-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5683-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5683-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f5683-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f5683-125">Nie ma wystarczającej ilości dostępnej pamięci na utworzyć żądany sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="f5683-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5683-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5683-126">Remarks</span></span>  
 <span data-ttu-id="f5683-127">Obiekty sekcję krytyczną zapewniają podobne do dostarczony przez obiekt mutex synchronizacji z tą różnicą, że sekcje krytyczne mogą korzystać tylko wątki pojedynczego procesu.</span><span class="sxs-lookup"><span data-stu-id="f5683-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> `CreateCrst` <span data-ttu-id="f5683-128">odzwierciedla Win32 `InitializeCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5683-128">mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5683-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5683-129">Requirements</span></span>  
 <span data-ttu-id="f5683-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5683-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5683-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5683-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5683-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5683-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f5683-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f5683-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5683-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5683-134">See also</span></span>

- [<span data-ttu-id="f5683-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5683-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f5683-136">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5683-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="f5683-137">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5683-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="f5683-138">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5683-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="f5683-139">Muteksy</span><span class="sxs-lookup"><span data-stu-id="f5683-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)
- [<span data-ttu-id="f5683-140">Semafor i klasa SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="f5683-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
