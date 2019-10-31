---
title: ICLRGCManager::GetStats — Metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 9e8b65c735028029f4fb44c2640df74ef171d9de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141143"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="9f06f-102">ICLRGCManager::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f06f-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="9f06f-103">Pobiera zestaw bieżących statystyk dotyczących systemu odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9f06f-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f06f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f06f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f06f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f06f-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="9f06f-106">[in. out] Wystąpienie [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) , które zawiera żądane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="9f06f-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f06f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9f06f-107">Return Value</span></span>  
  
|<span data-ttu-id="9f06f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f06f-108">HRESULT</span></span>|<span data-ttu-id="9f06f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9f06f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f06f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f06f-110">S_OK</span></span>|<span data-ttu-id="9f06f-111">`GetStats` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="9f06f-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="9f06f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f06f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f06f-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9f06f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f06f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f06f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f06f-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9f06f-115">The call timed out.</span></span>|  
|<span data-ttu-id="9f06f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f06f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f06f-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9f06f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f06f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f06f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f06f-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9f06f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f06f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f06f-120">E_FAIL</span></span>|<span data-ttu-id="9f06f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9f06f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f06f-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9f06f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f06f-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9f06f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f06f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f06f-124">Remarks</span></span>  
 <span data-ttu-id="9f06f-125">Środowisko CLR oblicza i zwraca tylko te statystyki, które są określone przez `Flags` pole `pStats`.</span><span class="sxs-lookup"><span data-stu-id="9f06f-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="9f06f-126">Ustaw wartość pola `Flags` na co najmniej jedną wartość wyliczenia [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby określić, które statystyki w strukturze [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) mają być ustawiane.</span><span class="sxs-lookup"><span data-stu-id="9f06f-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="9f06f-127">Przykładem użycia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="9f06f-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9f06f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f06f-128">Requirements</span></span>  
 <span data-ttu-id="9f06f-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f06f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f06f-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f06f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f06f-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f06f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f06f-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f06f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f06f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f06f-133">See also</span></span>

- [<span data-ttu-id="9f06f-134">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="9f06f-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="9f06f-135">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="9f06f-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="9f06f-136">COR_GC_STAT_TYPES, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9f06f-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="9f06f-137">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="9f06f-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="9f06f-138">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f06f-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9f06f-139">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f06f-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="9f06f-140">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="9f06f-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="9f06f-141">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9f06f-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9f06f-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="9f06f-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
