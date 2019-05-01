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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ef9a5896c2ecc54b7fd48670f751d193ac74554
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992722"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="8c1cf-102">IHostSyncManager::CreateSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c1cf-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="8c1cf-103">Tworzy [ihostsemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) obiektu środowisko uruchomieniowe języka wspólnego (CLR) do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c1cf-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c1cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c1cf-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="8c1cf-106">[in] Liczba początkowa `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="8c1cf-107">[in] Maksymalna liczba dla `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="8c1cf-108">[out] Wskaźnik na adres `IHostSemaphore` wystąpienia lub wartość null, jeśli nie można utworzyć semafora.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c1cf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8c1cf-109">Return Value</span></span>  
  
|<span data-ttu-id="8c1cf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c1cf-110">HRESULT</span></span>|<span data-ttu-id="8c1cf-111">Opis</span><span class="sxs-lookup"><span data-stu-id="8c1cf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c1cf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c1cf-112">S_OK</span></span>|<span data-ttu-id="8c1cf-113">`CreateSemaphore` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="8c1cf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c1cf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c1cf-115">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c1cf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c1cf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c1cf-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-117">The call timed out.</span></span>|  
|<span data-ttu-id="8c1cf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c1cf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c1cf-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c1cf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c1cf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c1cf-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c1cf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c1cf-122">E_FAIL</span></span>|<span data-ttu-id="8c1cf-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c1cf-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c1cf-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c1cf-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8c1cf-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8c1cf-127">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c1cf-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c1cf-128">Remarks</span></span>  
 <span data-ttu-id="8c1cf-129">`CreateSemaphore` odzwierciedla funkcję Win32, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="8c1cf-130">`dwInitial` i `dwMax` parametry korzysta z tej samej semantyki liczba semafora jako Win32 `lInitialCount` i `lMaximumCount` parametrów, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="8c1cf-131">`dwInitial` musi mieć długość od zera i `dwMax`włącznie.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="8c1cf-132">`dwMax` Musi być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="8c1cf-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c1cf-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c1cf-133">Requirements</span></span>  
 <span data-ttu-id="8c1cf-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c1cf-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c1cf-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c1cf-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c1cf-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c1cf-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c1cf-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c1cf-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1cf-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c1cf-138">See also</span></span>

- [<span data-ttu-id="8c1cf-139">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c1cf-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8c1cf-140">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c1cf-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8c1cf-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c1cf-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
