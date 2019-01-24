---
title: ICLRTask::YieldTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44716e0c763fe71fe94c8c0ec247cd37379561ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682894"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="e3b62-102">ICLRTask::YieldTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3b62-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="e3b62-103">Żądania, że środowisko uruchomieniowe języka wspólnego (CLR) odłożone zadania, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie reprezentuje i udostępnić czas procesora do innych zadań.</span><span class="sxs-lookup"><span data-stu-id="e3b62-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3b62-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e3b62-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3b62-105">Return Value</span></span>  
  
|<span data-ttu-id="e3b62-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3b62-106">HRESULT</span></span>|<span data-ttu-id="e3b62-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3b62-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3b62-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3b62-108">S_OK</span></span>|<span data-ttu-id="e3b62-109">`YieldTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e3b62-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="e3b62-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3b62-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3b62-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3b62-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3b62-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3b62-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3b62-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3b62-113">The call timed out.</span></span>|  
|<span data-ttu-id="e3b62-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3b62-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3b62-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e3b62-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3b62-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3b62-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3b62-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e3b62-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3b62-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3b62-118">E_FAIL</span></span>|<span data-ttu-id="e3b62-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e3b62-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3b62-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e3b62-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3b62-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3b62-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3b62-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3b62-122">Remarks</span></span>  
 <span data-ttu-id="e3b62-123">Wywołuje hosta `YieldTask` do żądania zasobów procesora dla innych zadań lub procesów.</span><span class="sxs-lookup"><span data-stu-id="e3b62-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="e3b62-124">Ta metoda jest przeznaczona głównie do długotrwałych kodu dać czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="e3b62-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="e3b62-125">Środowisko uruchomieniowe próbuje umieścić zadania, bieżący `ICLRTask` wystąpienie reprezentuje w stanie, w której ten może przynieść czas przetwarzania, ale nie gwarantuje sukces.</span><span class="sxs-lookup"><span data-stu-id="e3b62-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3b62-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3b62-126">Requirements</span></span>  
 <span data-ttu-id="e3b62-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3b62-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3b62-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3b62-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3b62-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3b62-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3b62-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3b62-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b62-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3b62-131">See also</span></span>
- [<span data-ttu-id="e3b62-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3b62-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e3b62-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3b62-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e3b62-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3b62-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e3b62-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3b62-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
