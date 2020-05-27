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
ms.openlocfilehash: 3566907544c72da2735e155d9088fe09fea4a728
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803475"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="63acc-102">IHostSyncManager::CreateCrst — Metoda</span><span class="sxs-lookup"><span data-stu-id="63acc-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="63acc-103">Tworzy obiekt sekcji krytycznej do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="63acc-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63acc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63acc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63acc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63acc-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="63acc-106">określoną Wskaźnik do adresu wystąpienia [IHostCrst](ihostcrst-interface.md) zaimplementowanego przez hosta lub wartość null, jeśli nie można utworzyć sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="63acc-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63acc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="63acc-107">Return Value</span></span>  
  
|<span data-ttu-id="63acc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63acc-108">HRESULT</span></span>|<span data-ttu-id="63acc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="63acc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63acc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="63acc-110">S_OK</span></span>|<span data-ttu-id="63acc-111">`CreateCrst`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="63acc-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="63acc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63acc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63acc-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="63acc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63acc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63acc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63acc-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="63acc-115">The call timed out.</span></span>|  
|<span data-ttu-id="63acc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63acc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63acc-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="63acc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63acc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63acc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63acc-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="63acc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63acc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63acc-120">E_FAIL</span></span>|<span data-ttu-id="63acc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="63acc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63acc-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="63acc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63acc-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="63acc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="63acc-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="63acc-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="63acc-125">Za mało dostępnej pamięci, aby utworzyć żądaną sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="63acc-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63acc-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63acc-126">Remarks</span></span>  
 <span data-ttu-id="63acc-127">Obiekty sekcji krytycznej zapewniają synchronizację podobną do tej, która jest dostarczana przez obiekt mutex, z tą różnicą, że sekcje krytyczne mogą być używane tylko przez wątki pojedynczego procesu.</span><span class="sxs-lookup"><span data-stu-id="63acc-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="63acc-128">`CreateCrst`odzwierciedla funkcję Win32 `InitializeCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="63acc-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63acc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63acc-129">Requirements</span></span>  
 <span data-ttu-id="63acc-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63acc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63acc-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63acc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63acc-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63acc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63acc-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63acc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63acc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63acc-134">See also</span></span>

- [<span data-ttu-id="63acc-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63acc-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="63acc-136">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="63acc-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="63acc-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="63acc-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="63acc-138">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="63acc-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="63acc-139">Muteksy</span><span class="sxs-lookup"><span data-stu-id="63acc-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="63acc-140">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="63acc-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
