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
ms.openlocfilehash: f8f476f681764a46700dd5ec83c8f9b2739f18f6
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842494"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="54a41-102">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="54a41-102">IHostTask Interface</span></span>
<span data-ttu-id="54a41-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) komunikowanie się z hostem w celu zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="54a41-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54a41-104">Metody</span><span class="sxs-lookup"><span data-stu-id="54a41-104">Methods</span></span>  
  
|<span data-ttu-id="54a41-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-105">Method</span></span>|<span data-ttu-id="54a41-106">Opis</span><span class="sxs-lookup"><span data-stu-id="54a41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54a41-107">Alert, metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="54a41-108">Żąda, aby Host wznowił zadanie reprezentowane przez bieżące `IHostTask` wystąpienie, więc zadanie można przerwać.</span><span class="sxs-lookup"><span data-stu-id="54a41-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="54a41-109">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="54a41-110">Pobiera poziom priorytetu wątku zadania reprezentowanego przez bieżące `IHostTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="54a41-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="54a41-111">Join, metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="54a41-112">Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące `IHostTask` wystąpienie, upłynie określony przedział czasu lub [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="54a41-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="54a41-113">SetCLRTask, metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="54a41-114">Kojarzy wystąpienie [interfejsu ICLRTask](iclrtask-interface.md) z bieżącym `IHostTask` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="54a41-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="54a41-115">SetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="54a41-116">Żądania, za pomocą których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące `IHostTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="54a41-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="54a41-117">Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="54a41-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="54a41-118">Żąda, aby Host przeniesieł zadanie reprezentowane przez bieżące `IHostTask` wystąpienie ze stanu wstrzymania do stanu na żywo, w którym można wykonać kod.</span><span class="sxs-lookup"><span data-stu-id="54a41-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54a41-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54a41-119">Remarks</span></span>  
 <span data-ttu-id="54a41-120">Środowisko CLR wywołuje metody zdefiniowane przez, `IHostTask` Aby uruchomić zadanie, ustawić jego poziom priorytetu wątku i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="54a41-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a41-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54a41-121">Requirements</span></span>  
 <span data-ttu-id="54a41-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a41-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a41-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54a41-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54a41-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54a41-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54a41-125">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a41-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a41-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54a41-126">See also</span></span>

- [<span data-ttu-id="54a41-127">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="54a41-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="54a41-128">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="54a41-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="54a41-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="54a41-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="54a41-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="54a41-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
