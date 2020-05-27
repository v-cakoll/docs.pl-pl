---
title: IHostSyncManager::CreateSemaphore — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803140"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="aa259-102">IHostSyncManager::CreateSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa259-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="aa259-103">Tworzy obiekt [IHostSemaphore](ihostsemaphore-interface.md) dla środowiska uruchomieniowego języka wspólnego (CLR) do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="aa259-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa259-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa259-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa259-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa259-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="aa259-106">podczas Początkowa liczba dla `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="aa259-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="aa259-107">podczas Maksymalna liczba dla `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="aa259-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="aa259-108">określoną Wskaźnik do adresu `IHostSemaphore` wystąpienia lub wartość null, jeśli nie można utworzyć semafora.</span><span class="sxs-lookup"><span data-stu-id="aa259-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa259-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa259-109">Return Value</span></span>  
  
|<span data-ttu-id="aa259-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa259-110">HRESULT</span></span>|<span data-ttu-id="aa259-111">Opis</span><span class="sxs-lookup"><span data-stu-id="aa259-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa259-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa259-112">S_OK</span></span>|<span data-ttu-id="aa259-113">`CreateSemaphore`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="aa259-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="aa259-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa259-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa259-115">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa259-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa259-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa259-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa259-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="aa259-117">The call timed out.</span></span>|  
|<span data-ttu-id="aa259-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa259-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa259-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="aa259-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa259-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa259-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa259-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="aa259-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa259-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa259-122">E_FAIL</span></span>|<span data-ttu-id="aa259-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa259-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa259-124">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="aa259-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa259-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa259-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa259-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aa259-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aa259-127">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aa259-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa259-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa259-128">Remarks</span></span>  
 <span data-ttu-id="aa259-129">`CreateSemaphore`odzwierciedla funkcję Win32, która ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="aa259-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="aa259-130">`dwInitial`Parametry i `dwMax` używają tej samej semantyki jako `lInitialCount` odpowiednio Win32 i `lMaximumCount` Parameters.</span><span class="sxs-lookup"><span data-stu-id="aa259-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="aa259-131">`dwInitial`musi zawierać się w przedziale od 0 do `dwMax` włącznie.</span><span class="sxs-lookup"><span data-stu-id="aa259-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="aa259-132">`dwMax`musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="aa259-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa259-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa259-133">Requirements</span></span>  
 <span data-ttu-id="aa259-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa259-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa259-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa259-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa259-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa259-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa259-137">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa259-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa259-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa259-138">See also</span></span>

- [<span data-ttu-id="aa259-139">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="aa259-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="aa259-140">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa259-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="aa259-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa259-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
