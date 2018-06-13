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
ms.openlocfilehash: 96673049d37034781dff9f206db86a1d5d953d52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436403"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="3beb3-102">ICLRGCManager::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="3beb3-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="3beb3-103">Pobiera zestaw bieżącego Statystyka system czyszczenia pamięci środowisko uruchomieniowe języka wspólnego firmy.</span><span class="sxs-lookup"><span data-stu-id="3beb3-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3beb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3beb3-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3beb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3beb3-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="3beb3-106">[w, out] A [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) wystąpienia, które zawiera wymaganych danych statystycznych.</span><span class="sxs-lookup"><span data-stu-id="3beb3-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3beb3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3beb3-107">Return Value</span></span>  
  
|<span data-ttu-id="3beb3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3beb3-108">HRESULT</span></span>|<span data-ttu-id="3beb3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3beb3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3beb3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3beb3-110">S_OK</span></span>|<span data-ttu-id="3beb3-111">`GetStats` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3beb3-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="3beb3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3beb3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3beb3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3beb3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3beb3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3beb3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3beb3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3beb3-115">The call timed out.</span></span>|  
|<span data-ttu-id="3beb3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3beb3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3beb3-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3beb3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3beb3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3beb3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3beb3-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3beb3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3beb3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3beb3-120">E_FAIL</span></span>|<span data-ttu-id="3beb3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3beb3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3beb3-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3beb3-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3beb3-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3beb3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3beb3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3beb3-124">Remarks</span></span>  
 <span data-ttu-id="3beb3-125">Środowisko CLR oblicza i zwraca tylko te statystyki, które są określone przez `Flags` pole `pStats`.</span><span class="sxs-lookup"><span data-stu-id="3beb3-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="3beb3-126">Ustaw `Flags` pola na jedną lub więcej wartości [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczeniu, aby określić, które statystyki w [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mają być tworzone.</span><span class="sxs-lookup"><span data-stu-id="3beb3-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="3beb3-127">Przykład użycia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3beb3-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3beb3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3beb3-128">Requirements</span></span>  
 <span data-ttu-id="3beb3-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3beb3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3beb3-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3beb3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3beb3-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3beb3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3beb3-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3beb3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3beb3-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3beb3-133">See Also</span></span>  
 [<span data-ttu-id="3beb3-134">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="3beb3-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="3beb3-135">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="3beb3-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="3beb3-136">COR_GC_STAT_TYPES, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3beb3-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="3beb3-137">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="3beb3-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="3beb3-138">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="3beb3-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3beb3-139">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3beb3-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="3beb3-140">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="3beb3-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="3beb3-141">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3beb3-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="3beb3-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="3beb3-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
