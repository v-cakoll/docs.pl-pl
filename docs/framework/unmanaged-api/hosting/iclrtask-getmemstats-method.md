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
ms.openlocfilehash: d2284a311f8355b65f312112db9cddd458517b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433895"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="d9412-102">ICLRTask::GetMemStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9412-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="d9412-103">Pobiera informacje o użyciu pamięci statystyczne powiązanego z zadaniem który bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) reprezentuje wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d9412-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9412-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9412-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9412-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9412-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="d9412-106">[out] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) wystąpienia, które zawiera szczegółowe informacje o użyciu pamięci zadania, w tym liczba bajtów przydzielonych.</span><span class="sxs-lookup"><span data-stu-id="d9412-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9412-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d9412-107">Return Value</span></span>  
  
|<span data-ttu-id="d9412-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9412-108">HRESULT</span></span>|<span data-ttu-id="d9412-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d9412-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9412-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9412-110">S_OK</span></span>|<span data-ttu-id="d9412-111">`GetMemStats` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d9412-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="d9412-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9412-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9412-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d9412-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9412-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9412-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9412-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d9412-115">The call timed out.</span></span>|  
|<span data-ttu-id="d9412-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9412-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9412-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d9412-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9412-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9412-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9412-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d9412-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9412-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9412-120">E_FAIL</span></span>|<span data-ttu-id="d9412-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d9412-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9412-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d9412-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9412-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9412-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9412-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9412-124">Requirements</span></span>  
 <span data-ttu-id="d9412-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9412-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9412-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9412-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9412-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9412-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9412-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9412-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9412-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9412-129">See Also</span></span>  
 [<span data-ttu-id="d9412-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9412-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d9412-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9412-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d9412-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9412-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d9412-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9412-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
