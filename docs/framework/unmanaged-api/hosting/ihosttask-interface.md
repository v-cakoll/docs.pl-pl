---
title: IHostTask — Interfejs
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttask-interface"></a><span data-ttu-id="cf66f-102">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cf66f-102">IHostTask Interface</span></span>
<span data-ttu-id="cf66f-103">Udostępnia metody umożliwiające środowisko uruchomieniowe języka wspólnego (CLR) do komunikacji z hostem, do zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="cf66f-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf66f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cf66f-104">Methods</span></span>  
  
|<span data-ttu-id="cf66f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-105">Method</span></span>|<span data-ttu-id="cf66f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cf66f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf66f-107">Alert, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="cf66f-108">Żądania, że host wake reprezentowany przez bieżące zadanie `IHostTask` wystąpienia, zadania można zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="cf66f-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="cf66f-109">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="cf66f-110">Pobiera poziom priorytetu wątku zadania reprezentowany przez bieżący `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cf66f-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="cf66f-111">Join, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="cf66f-112">Blokuje wywoływania zadań dopóki reprezentowany przez bieżące zadanie `IHostTask` zakończeniu wystąpienia, upłynie określony interwał, lub [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="cf66f-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="cf66f-113">SetCLRTask, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="cf66f-114">Kojarzy [ICLRTask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia z bieżącym `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cf66f-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="cf66f-115">SetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="cf66f-116">Żądania, że host dostosować priorytetu wątku poziomu reprezentowanego przez bieżącego zadania `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cf66f-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="cf66f-117">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="cf66f-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="cf66f-118">Żądania, że host move — zadanie reprezentowany przez bieżący `IHostTask` wystąpienie ze stanu wstrzymania do aktywnego stanu, w którym można wykonywać kodu.</span><span class="sxs-lookup"><span data-stu-id="cf66f-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf66f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf66f-119">Remarks</span></span>  
 <span data-ttu-id="cf66f-120">Środowisko CLR wywołuje metody zdefiniowane przez `IHostTask` można uruchomić zadania, jego priorytetu wątku ustaw poziom itd.</span><span class="sxs-lookup"><span data-stu-id="cf66f-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf66f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf66f-121">Requirements</span></span>  
 <span data-ttu-id="cf66f-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf66f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf66f-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf66f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf66f-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf66f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf66f-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf66f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf66f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf66f-126">See Also</span></span>  
 [<span data-ttu-id="cf66f-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf66f-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cf66f-128">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf66f-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cf66f-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf66f-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cf66f-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cf66f-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
