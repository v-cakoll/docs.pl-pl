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
ms.openlocfilehash: 7eb5c7ec85c0adb301fb722155caaed3c14e0e19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137725"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="d83f9-102">IHostTaskManager::BeginThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="d83f9-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="d83f9-103">Powiadamia hosta, którego kod zarządzany wchodzi okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d83f9-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d83f9-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d83f9-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d83f9-105">Return Value</span></span>  
  
|<span data-ttu-id="d83f9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d83f9-106">HRESULT</span></span>|<span data-ttu-id="d83f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d83f9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d83f9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d83f9-108">S_OK</span></span>|`BeginThreadAffinity` <span data-ttu-id="d83f9-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d83f9-109">returned successfully.</span></span>|  
|<span data-ttu-id="d83f9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d83f9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d83f9-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d83f9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d83f9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d83f9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d83f9-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d83f9-113">The call timed out.</span></span>|  
|<span data-ttu-id="d83f9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d83f9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d83f9-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d83f9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d83f9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d83f9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d83f9-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d83f9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d83f9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d83f9-118">E_FAIL</span></span>|<span data-ttu-id="d83f9-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d83f9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d83f9-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d83f9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d83f9-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d83f9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d83f9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d83f9-122">Remarks</span></span>  
 <span data-ttu-id="d83f9-123">Środowisko CLR jest zazwyczaj wywołuje `IHostTaskManager::BeginThreadAffinity` w kontekście wywołanie <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d83f9-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d83f9-124">Bieżące zadanie nie musi ponownie, dopóki odpowiednie połączenie jest nawiązywane w przypadku [ihosttaskmanager::endthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="d83f9-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="d83f9-125">Zadania mogą być przełączane w poziomie, ale podczas przełączania w ich muszą być przypisane do tego samego wątku systemu operacyjnego, w którym zostały przełączenie. Zagnieżdżone wywołania `BeginThreadAffinity` miało żadnego efektu, ponieważ wywołanie odnosi się do bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="d83f9-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83f9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d83f9-126">Requirements</span></span>  
 <span data-ttu-id="d83f9-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83f9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83f9-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d83f9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d83f9-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d83f9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d83f9-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d83f9-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d83f9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d83f9-131">See also</span></span>

- [<span data-ttu-id="d83f9-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d83f9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d83f9-133">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d83f9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d83f9-134">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d83f9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d83f9-135">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d83f9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
