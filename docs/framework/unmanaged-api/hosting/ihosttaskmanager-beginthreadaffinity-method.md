---
title: IHostTaskManager::BeginThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67a133604e269b8c20dc8640b91e378c498cf038
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745585"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="8ae5d-102">IHostTaskManager::BeginThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ae5d-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="8ae5d-103">Powiadamia hosta, którego kod zarządzany wchodzi okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ae5d-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8ae5d-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ae5d-105">Return Value</span></span>  
  
|<span data-ttu-id="8ae5d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ae5d-106">HRESULT</span></span>|<span data-ttu-id="8ae5d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae5d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ae5d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ae5d-108">S_OK</span></span>|<span data-ttu-id="8ae5d-109">`BeginThreadAffinity` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="8ae5d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ae5d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ae5d-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ae5d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ae5d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ae5d-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-113">The call timed out.</span></span>|  
|<span data-ttu-id="8ae5d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ae5d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ae5d-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ae5d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ae5d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ae5d-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ae5d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ae5d-118">E_FAIL</span></span>|<span data-ttu-id="8ae5d-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ae5d-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ae5d-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ae5d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ae5d-122">Remarks</span></span>  
 <span data-ttu-id="8ae5d-123">Środowisko CLR jest zazwyczaj wywołuje `IHostTaskManager::BeginThreadAffinity` w kontekście wywołanie <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ae5d-124">Bieżące zadanie nie musi ponownie, dopóki odpowiednie połączenie jest nawiązywane w przypadku [ihosttaskmanager::endthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ae5d-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="8ae5d-125">Zadania mogą być przełączane w poziomie, ale podczas przełączania w ich muszą być przypisane do tego samego wątku systemu operacyjnego, w którym zostały przełączenie. Zagnieżdżone wywołania `BeginThreadAffinity` miało żadnego efektu, ponieważ wywołanie odnosi się do bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="8ae5d-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ae5d-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ae5d-126">Requirements</span></span>  
 <span data-ttu-id="8ae5d-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae5d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae5d-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ae5d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ae5d-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ae5d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ae5d-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae5d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae5d-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ae5d-131">See also</span></span>
- [<span data-ttu-id="8ae5d-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ae5d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8ae5d-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ae5d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8ae5d-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ae5d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8ae5d-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ae5d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
