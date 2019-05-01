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
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992839"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="90274-102">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="90274-102">IHostTask Interface</span></span>
<span data-ttu-id="90274-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do komunikacji z hostem, do zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="90274-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90274-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90274-104">Methods</span></span>  
  
|<span data-ttu-id="90274-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90274-105">Method</span></span>|<span data-ttu-id="90274-106">Opis</span><span class="sxs-lookup"><span data-stu-id="90274-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90274-107">Alert, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="90274-108">Żądania, czy host wznawiania zadania, reprezentowane przez bieżącą `IHostTask` wystąpienie, dlatego zadanie może zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="90274-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="90274-109">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="90274-110">Pobiera poziom priorytetu wątku zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="90274-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="90274-111">Join, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="90274-112">Blokuje wywołującym je zadaniem i do zadań, reprezentowane przez bieżącą `IHostTask` ukończenia wystąpienia, przez określony interwał czasu upłynie, lub [ihosttask::alert —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="90274-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="90274-113">SetCLRTask, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="90274-114">Kojarzy [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia z bieżącymi `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="90274-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="90274-115">SetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="90274-116">Na poziomie żądania, czy host zmienić priorytet wątku dla zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="90274-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="90274-117">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="90274-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="90274-118">Żądania, że host move — zadanie, reprezentowane przez bieżącą `IHostTask` wystąpienia ze stanu wstrzymania Państwu na żywo, w którym można wykonywać kodu.</span><span class="sxs-lookup"><span data-stu-id="90274-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90274-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90274-119">Remarks</span></span>  
 <span data-ttu-id="90274-120">Środowisko CLR wywołuje metody zdefiniowane przez `IHostTask` można uruchomić zadania, ustaw jego priorytetu wątku poziom, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="90274-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90274-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90274-121">Requirements</span></span>  
 <span data-ttu-id="90274-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90274-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90274-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90274-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90274-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90274-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90274-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90274-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90274-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90274-126">See also</span></span>

- [<span data-ttu-id="90274-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="90274-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="90274-128">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="90274-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="90274-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="90274-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="90274-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="90274-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
