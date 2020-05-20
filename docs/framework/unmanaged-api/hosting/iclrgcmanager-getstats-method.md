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
ms.openlocfilehash: 1e881b4a55a99bac3f9ca0e8db1556807b888f13
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616973"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="b51ce-102">ICLRGCManager::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="b51ce-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="b51ce-103">Pobiera zestaw bieżących statystyk dotyczących systemu odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b51ce-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b51ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b51ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b51ce-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="b51ce-106">[in. out] Wystąpienie [COR_GC_STATS](cor-gc-stats-structure.md) , które zawiera żądane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="b51ce-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b51ce-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b51ce-107">Return Value</span></span>  
  
|<span data-ttu-id="b51ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b51ce-108">HRESULT</span></span>|<span data-ttu-id="b51ce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b51ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b51ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b51ce-110">S_OK</span></span>|<span data-ttu-id="b51ce-111">`GetStats`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b51ce-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="b51ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b51ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b51ce-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b51ce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b51ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b51ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b51ce-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b51ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="b51ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b51ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b51ce-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b51ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b51ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b51ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b51ce-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b51ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b51ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b51ce-120">E_FAIL</span></span>|<span data-ttu-id="b51ce-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b51ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b51ce-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="b51ce-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b51ce-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b51ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b51ce-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b51ce-124">Remarks</span></span>  
 <span data-ttu-id="b51ce-125">Środowisko CLR oblicza i zwraca tylko te statystyki, które są określone w `Flags` polu `pStats` .</span><span class="sxs-lookup"><span data-stu-id="b51ce-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="b51ce-126">Ustaw wartość `Flags` pola na co najmniej jedną wartość wyliczenia [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby określić, które statystyki w strukturze [COR_GC_STATS](cor-gc-stats-structure.md) mają być ustawione.</span><span class="sxs-lookup"><span data-stu-id="b51ce-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="b51ce-127">Przykładem użycia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="b51ce-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b51ce-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b51ce-128">Requirements</span></span>  
 <span data-ttu-id="b51ce-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b51ce-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b51ce-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b51ce-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b51ce-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b51ce-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b51ce-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b51ce-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51ce-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b51ce-133">See also</span></span>

- [<span data-ttu-id="b51ce-134">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="b51ce-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b51ce-135">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="b51ce-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="b51ce-136">COR_GC_STAT_TYPES, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b51ce-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="b51ce-137">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="b51ce-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b51ce-138">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b51ce-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b51ce-139">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b51ce-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="b51ce-140">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b51ce-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="b51ce-141">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b51ce-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b51ce-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="b51ce-142">Hosting</span></span>](index.md)
