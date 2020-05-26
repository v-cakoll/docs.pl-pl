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
ms.openlocfilehash: 86bc320c28a5fbf122d234a4a1f15b674628c0b5
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803399"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="5ae5d-102">IHostSyncManager::CreateCrstWithSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ae5d-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="5ae5d-103">Tworzy obiekt sekcji krytycznej z liczbą wirowania do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ae5d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ae5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ae5d-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="5ae5d-106">podczas Określa liczbę obrotów dla obiektu sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="5ae5d-107">określoną Wskaźnik do adresu wystąpienia [IHostCrst](ihostcrst-interface.md) lub wartość null, jeśli nie można utworzyć sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ae5d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5ae5d-108">Return Value</span></span>  
  
|<span data-ttu-id="5ae5d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ae5d-109">HRESULT</span></span>|<span data-ttu-id="5ae5d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5ae5d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ae5d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ae5d-111">S_OK</span></span>|<span data-ttu-id="5ae5d-112">`CreateCrstWithSpinCount`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="5ae5d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ae5d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ae5d-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ae5d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ae5d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ae5d-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-116">The call timed out.</span></span>|  
|<span data-ttu-id="5ae5d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ae5d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ae5d-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ae5d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ae5d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ae5d-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ae5d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ae5d-121">E_FAIL</span></span>|<span data-ttu-id="5ae5d-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ae5d-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ae5d-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ae5d-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5ae5d-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5ae5d-126">Za mało dostępnej pamięci, aby utworzyć żądaną sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ae5d-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ae5d-127">Remarks</span></span>  
 <span data-ttu-id="5ae5d-128">Liczba pokrętła jest używana tylko w systemie wieloprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="5ae5d-129">Liczba obrotów określa, ile razy wątek wywołujący musi się obrócić przed wykonaniem operacji oczekiwania dla semafora skojarzonego z niedostępną sekcją krytyczną.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="5ae5d-130">Jeśli Sekcja krytyczna zostanie zwolniona podczas operacji pokrętła, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5ae5d-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="5ae5d-131">`CreateCrstWithSpinCount`odzwierciedla funkcję Win32 `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="5ae5d-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ae5d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ae5d-132">Requirements</span></span>  
 <span data-ttu-id="5ae5d-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ae5d-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ae5d-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ae5d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ae5d-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ae5d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ae5d-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ae5d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae5d-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ae5d-137">See also</span></span>

- [<span data-ttu-id="5ae5d-138">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5d-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="5ae5d-139">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5d-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="5ae5d-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5d-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
