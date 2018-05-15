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
ms.openlocfilehash: 6a94797e6279a1f1d419b977c22d73ca41bbafc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="0cb79-102">IHostTaskManager::BeginThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="0cb79-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="0cb79-103">Powiadamia hosta, którego kod zarządzany jest wprowadzanie okres, w którym bieżącego zadania nie muszą zostać przeniesione do innego wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0cb79-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cb79-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0cb79-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0cb79-105">Return Value</span></span>  
  
|<span data-ttu-id="0cb79-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cb79-106">HRESULT</span></span>|<span data-ttu-id="0cb79-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0cb79-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cb79-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cb79-108">S_OK</span></span>|<span data-ttu-id="0cb79-109">`BeginThreadAffinity` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0cb79-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="0cb79-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0cb79-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0cb79-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0cb79-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0cb79-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0cb79-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0cb79-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0cb79-113">The call timed out.</span></span>|  
|<span data-ttu-id="0cb79-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0cb79-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0cb79-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0cb79-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0cb79-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0cb79-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0cb79-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0cb79-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0cb79-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cb79-118">E_FAIL</span></span>|<span data-ttu-id="0cb79-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0cb79-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0cb79-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0cb79-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0cb79-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0cb79-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb79-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cb79-122">Remarks</span></span>  
 <span data-ttu-id="0cb79-123">Zazwyczaj wymaga środowiska CLR `IHostTaskManager::BeginThreadAffinity` w kontekście wywołania <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0cb79-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0cb79-124">Bieżące zadanie musi nie można przeprowadzić, aż do dokonania odpowiedniego wywołania do [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="0cb79-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="0cb79-125">Zadania mogą być przełączane wychodzących, ale podczas przełączania w ich muszą być przypisane do tego samego wątku systemu operacyjnego, w którym zostały przełączone limit. Zagnieżdżone wywołania `BeginThreadAffinity` nie mają wpływu, ponieważ wywołanie odwołuje się do bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="0cb79-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb79-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0cb79-126">Requirements</span></span>  
 <span data-ttu-id="0cb79-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb79-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb79-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cb79-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cb79-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0cb79-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cb79-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb79-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb79-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cb79-131">See Also</span></span>  
 [<span data-ttu-id="0cb79-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb79-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0cb79-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb79-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0cb79-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb79-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0cb79-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb79-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
