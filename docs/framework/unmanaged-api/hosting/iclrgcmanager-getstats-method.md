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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e92707e7b24709d64915e29823196bb0f827175
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485243"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="3e587-102">ICLRGCManager::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="3e587-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="3e587-103">Pobiera zestaw statystyk bieżące informacje o systemie kolekcji wyrzucania elementów wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="3e587-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e587-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e587-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e587-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e587-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="3e587-106">[out w] A [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) wystąpienia, które zawiera żądane statystyk.</span><span class="sxs-lookup"><span data-stu-id="3e587-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e587-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3e587-107">Return Value</span></span>  
  
|<span data-ttu-id="3e587-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e587-108">HRESULT</span></span>|<span data-ttu-id="3e587-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3e587-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e587-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e587-110">S_OK</span></span>|<span data-ttu-id="3e587-111">`GetStats` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="3e587-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="3e587-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e587-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e587-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3e587-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e587-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e587-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e587-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3e587-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e587-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e587-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e587-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="3e587-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e587-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e587-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e587-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3e587-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e587-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e587-120">E_FAIL</span></span>|<span data-ttu-id="3e587-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3e587-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e587-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3e587-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e587-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e587-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e587-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e587-124">Remarks</span></span>  
 <span data-ttu-id="3e587-125">Środowisko CLR oblicza i zwraca tylko te statystyki, które są określone przez `Flags` pole `pStats`.</span><span class="sxs-lookup"><span data-stu-id="3e587-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="3e587-126">Ustaw `Flags` pole jedną lub więcej wartości [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczeniu, aby określić, które statystyki w [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mają być tworzone.</span><span class="sxs-lookup"><span data-stu-id="3e587-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="3e587-127">Przykład użycia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3e587-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3e587-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e587-128">Requirements</span></span>  
 <span data-ttu-id="3e587-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e587-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e587-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e587-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e587-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e587-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e587-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e587-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e587-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e587-133">See also</span></span>
- [<span data-ttu-id="3e587-134">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="3e587-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="3e587-135">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="3e587-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="3e587-136">COR_GC_STAT_TYPES, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3e587-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="3e587-137">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="3e587-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="3e587-138">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e587-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3e587-139">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e587-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="3e587-140">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="3e587-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="3e587-141">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3e587-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3e587-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="3e587-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
