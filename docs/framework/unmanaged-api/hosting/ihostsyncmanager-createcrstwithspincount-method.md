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
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139410"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="ffad8-102">IHostSyncManager::CreateCrstWithSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffad8-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="ffad8-103">Tworzy obiekt sekcji krytycznej z liczbą wirowania do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="ffad8-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffad8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffad8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffad8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffad8-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="ffad8-106">podczas Określa liczbę obrotów dla obiektu sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="ffad8-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="ffad8-107">określoną Wskaźnik do adresu wystąpienia [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) lub wartość null, jeśli nie można utworzyć sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="ffad8-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffad8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ffad8-108">Return Value</span></span>  
  
|<span data-ttu-id="ffad8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffad8-109">HRESULT</span></span>|<span data-ttu-id="ffad8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ffad8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffad8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffad8-111">S_OK</span></span>|<span data-ttu-id="ffad8-112">`CreateCrstWithSpinCount` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="ffad8-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="ffad8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffad8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffad8-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ffad8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffad8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffad8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffad8-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ffad8-116">The call timed out.</span></span>|  
|<span data-ttu-id="ffad8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffad8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffad8-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ffad8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffad8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffad8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffad8-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ffad8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffad8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffad8-121">E_FAIL</span></span>|<span data-ttu-id="ffad8-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ffad8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffad8-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="ffad8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffad8-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ffad8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ffad8-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ffad8-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ffad8-126">Za mało dostępnej pamięci, aby utworzyć żądaną sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="ffad8-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffad8-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffad8-127">Remarks</span></span>  
 <span data-ttu-id="ffad8-128">Liczba pokrętła jest używana tylko w systemie wieloprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="ffad8-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="ffad8-129">Liczba obrotów określa, ile razy wątek wywołujący musi się obrócić przed wykonaniem operacji oczekiwania dla semafora skojarzonego z niedostępną sekcją krytyczną.</span><span class="sxs-lookup"><span data-stu-id="ffad8-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="ffad8-130">Jeśli Sekcja krytyczna zostanie zwolniona podczas operacji pokrętła, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="ffad8-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="ffad8-131">`CreateCrstWithSpinCount` odzwierciedla funkcję Win32 `InitializeCriticalSectionAndSpinCount`.</span><span class="sxs-lookup"><span data-stu-id="ffad8-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffad8-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffad8-132">Requirements</span></span>  
 <span data-ttu-id="ffad8-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffad8-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffad8-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ffad8-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffad8-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ffad8-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffad8-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffad8-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffad8-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffad8-137">See also</span></span>

- [<span data-ttu-id="ffad8-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffad8-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ffad8-139">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffad8-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="ffad8-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffad8-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
