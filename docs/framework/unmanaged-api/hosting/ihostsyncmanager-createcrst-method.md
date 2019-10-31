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
ms.openlocfilehash: 03c0f94d10629b677cca4c4c456cdaab344cfcdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139432"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="5e114-102">IHostSyncManager::CreateCrst — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e114-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="5e114-103">Tworzy obiekt sekcji krytycznej do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="5e114-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e114-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e114-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e114-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e114-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="5e114-106">określoną Wskaźnik do adresu wystąpienia [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) zaimplementowanego przez hosta lub wartość null, jeśli nie można utworzyć sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="5e114-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e114-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e114-107">Return Value</span></span>  
  
|<span data-ttu-id="5e114-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e114-108">HRESULT</span></span>|<span data-ttu-id="5e114-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5e114-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e114-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e114-110">S_OK</span></span>|<span data-ttu-id="5e114-111">`CreateCrst` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="5e114-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="5e114-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e114-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e114-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5e114-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e114-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e114-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e114-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5e114-115">The call timed out.</span></span>|  
|<span data-ttu-id="5e114-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e114-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e114-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5e114-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e114-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e114-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e114-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5e114-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e114-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e114-120">E_FAIL</span></span>|<span data-ttu-id="5e114-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5e114-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e114-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="5e114-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e114-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e114-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e114-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5e114-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5e114-125">Za mało dostępnej pamięci, aby utworzyć żądaną sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="5e114-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e114-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e114-126">Remarks</span></span>  
 <span data-ttu-id="5e114-127">Obiekty sekcji krytycznej zapewniają synchronizację podobną do tej, która jest dostarczana przez obiekt mutex, z tą różnicą, że sekcje krytyczne mogą być używane tylko przez wątki pojedynczego procesu.</span><span class="sxs-lookup"><span data-stu-id="5e114-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="5e114-128">`CreateCrst` odzwierciedla funkcję Win32 `InitializeCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="5e114-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e114-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e114-129">Requirements</span></span>  
 <span data-ttu-id="5e114-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e114-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e114-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e114-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e114-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5e114-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e114-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e114-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e114-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e114-134">See also</span></span>

- [<span data-ttu-id="5e114-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e114-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5e114-136">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e114-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="5e114-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e114-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="5e114-138">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e114-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="5e114-139">Muteksy</span><span class="sxs-lookup"><span data-stu-id="5e114-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="5e114-140">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="5e114-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
