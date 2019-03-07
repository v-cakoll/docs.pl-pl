---
title: ICLRTask::GetMemStats — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86aa020b2fac6d1405d8f24488184f3f7dd618a1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471566"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="3c9d3-102">ICLRTask::GetMemStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c9d3-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="3c9d3-103">Pobiera informacje o użyciu pamięci statystyczne powiązanych z zadaniem, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c9d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c9d3-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c9d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c9d3-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="3c9d3-106">[out] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) wystąpienia, które zawiera szczegółowe informacje dotyczące użycia pamięci przez zadania, takie jak liczba przydzielonych bajtów.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c9d3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c9d3-107">Return Value</span></span>  
  
|<span data-ttu-id="3c9d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c9d3-108">HRESULT</span></span>|<span data-ttu-id="3c9d3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3c9d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c9d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c9d3-110">S_OK</span></span>|<span data-ttu-id="3c9d3-111">`GetMemStats` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="3c9d3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c9d3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c9d3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c9d3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c9d3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c9d3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-115">The call timed out.</span></span>|  
|<span data-ttu-id="3c9d3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c9d3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c9d3-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c9d3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c9d3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c9d3-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c9d3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c9d3-120">E_FAIL</span></span>|<span data-ttu-id="3c9d3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c9d3-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c9d3-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c9d3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c9d3-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c9d3-124">Requirements</span></span>  
 <span data-ttu-id="3c9d3-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c9d3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c9d3-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c9d3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c9d3-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c9d3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c9d3-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c9d3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9d3-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c9d3-129">See also</span></span>
- [<span data-ttu-id="3c9d3-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c9d3-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3c9d3-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c9d3-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3c9d3-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c9d3-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3c9d3-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c9d3-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
