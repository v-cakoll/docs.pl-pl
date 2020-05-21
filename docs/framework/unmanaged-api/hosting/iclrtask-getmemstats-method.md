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
ms.openlocfilehash: 0d2975d6247cd9ecdb07b564d77518151404c7d0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762466"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="2d613-102">ICLRTask::GetMemStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d613-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="2d613-103">Pobiera statystyczne informacje o wykorzystaniu pamięci powiązane z zadaniem, które reprezentuje bieżące wystąpienie [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2d613-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d613-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d613-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d613-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d613-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="2d613-106">określoną Wskaźnik do wystąpienia [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , który zawiera szczegółowe informacje o użyciu pamięci zadania, w tym liczbę przydzieloną bajtów.</span><span class="sxs-lookup"><span data-stu-id="2d613-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d613-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2d613-107">Return Value</span></span>  
  
|<span data-ttu-id="2d613-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d613-108">HRESULT</span></span>|<span data-ttu-id="2d613-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2d613-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d613-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d613-110">S_OK</span></span>|<span data-ttu-id="2d613-111">`GetMemStats`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2d613-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="2d613-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d613-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d613-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2d613-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d613-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d613-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d613-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2d613-115">The call timed out.</span></span>|  
|<span data-ttu-id="2d613-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d613-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d613-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2d613-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d613-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d613-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d613-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2d613-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d613-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d613-120">E_FAIL</span></span>|<span data-ttu-id="2d613-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2d613-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d613-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2d613-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d613-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d613-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d613-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d613-124">Requirements</span></span>  
 <span data-ttu-id="2d613-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d613-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d613-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d613-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d613-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d613-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d613-128">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d613-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d613-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d613-129">See also</span></span>

- [<span data-ttu-id="2d613-130">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d613-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2d613-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d613-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2d613-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d613-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2d613-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d613-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
