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
ms.openlocfilehash: 6a6383761b878c7e916064f9a046641d00a1c6ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734271"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="53ae2-102">ICLRTask::GetMemStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="53ae2-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="53ae2-103">Pobiera informacje o użyciu pamięci statystyczne powiązanych z zadaniem, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="53ae2-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ae2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53ae2-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53ae2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53ae2-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="53ae2-106">[out] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) wystąpienia, które zawiera szczegółowe informacje dotyczące użycia pamięci przez zadania, takie jak liczba przydzielonych bajtów.</span><span class="sxs-lookup"><span data-stu-id="53ae2-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53ae2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53ae2-107">Return Value</span></span>  
  
|<span data-ttu-id="53ae2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53ae2-108">HRESULT</span></span>|<span data-ttu-id="53ae2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="53ae2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53ae2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="53ae2-110">S_OK</span></span>|<span data-ttu-id="53ae2-111">`GetMemStats` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="53ae2-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="53ae2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53ae2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53ae2-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="53ae2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53ae2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53ae2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53ae2-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="53ae2-115">The call timed out.</span></span>|  
|<span data-ttu-id="53ae2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53ae2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53ae2-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="53ae2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53ae2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53ae2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53ae2-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="53ae2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53ae2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53ae2-120">E_FAIL</span></span>|<span data-ttu-id="53ae2-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="53ae2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53ae2-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="53ae2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53ae2-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53ae2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53ae2-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53ae2-124">Requirements</span></span>  
 <span data-ttu-id="53ae2-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53ae2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ae2-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53ae2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53ae2-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53ae2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53ae2-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ae2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ae2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53ae2-129">See also</span></span>
- [<span data-ttu-id="53ae2-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="53ae2-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="53ae2-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="53ae2-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="53ae2-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="53ae2-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="53ae2-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="53ae2-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
