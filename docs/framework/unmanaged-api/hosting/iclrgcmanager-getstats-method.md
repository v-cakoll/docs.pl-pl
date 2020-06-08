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
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504228"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="b66b3-102">ICLRGCManager::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="b66b3-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="b66b3-103">Pobiera zestaw bieżących statystyk dotyczących systemu odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b66b3-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b66b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b66b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b66b3-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="b66b3-106">[in. out] Wystąpienie [COR_GC_STATS](cor-gc-stats-structure.md) , które zawiera żądane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="b66b3-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b66b3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b66b3-107">Return Value</span></span>  
  
|<span data-ttu-id="b66b3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b66b3-108">HRESULT</span></span>|<span data-ttu-id="b66b3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b66b3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b66b3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b66b3-110">S_OK</span></span>|<span data-ttu-id="b66b3-111">`GetStats`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b66b3-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="b66b3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b66b3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b66b3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b66b3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b66b3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b66b3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b66b3-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b66b3-115">The call timed out.</span></span>|  
|<span data-ttu-id="b66b3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b66b3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b66b3-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b66b3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b66b3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b66b3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b66b3-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b66b3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b66b3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b66b3-120">E_FAIL</span></span>|<span data-ttu-id="b66b3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b66b3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b66b3-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="b66b3-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b66b3-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b66b3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b66b3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b66b3-124">Remarks</span></span>  
 <span data-ttu-id="b66b3-125">Środowisko CLR oblicza i zwraca tylko te statystyki, które są określone w `Flags` polu `pStats` .</span><span class="sxs-lookup"><span data-stu-id="b66b3-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="b66b3-126">Ustaw wartość `Flags` pola na co najmniej jedną wartość wyliczenia [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , aby określić, które statystyki w strukturze [COR_GC_STATS](cor-gc-stats-structure.md) mają być ustawione.</span><span class="sxs-lookup"><span data-stu-id="b66b3-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="b66b3-127">Przykładem użycia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="b66b3-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b66b3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b66b3-128">Requirements</span></span>  
 <span data-ttu-id="b66b3-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b66b3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b66b3-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b66b3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b66b3-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b66b3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b66b3-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b66b3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66b3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b66b3-133">See also</span></span>

- [<span data-ttu-id="b66b3-134">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="b66b3-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b66b3-135">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="b66b3-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="b66b3-136">COR_GC_STAT_TYPES, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b66b3-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="b66b3-137">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="b66b3-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b66b3-138">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b66b3-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b66b3-139">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b66b3-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="b66b3-140">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b66b3-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="b66b3-141">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b66b3-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b66b3-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="b66b3-142">Hosting</span></span>](index.md)
