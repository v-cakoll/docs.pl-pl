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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121394"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="d2a67-102">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d2a67-102">IHostTask Interface</span></span>
<span data-ttu-id="d2a67-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) komunikowanie się z hostem w celu zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="d2a67-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2a67-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d2a67-104">Methods</span></span>  
  
|<span data-ttu-id="d2a67-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-105">Method</span></span>|<span data-ttu-id="d2a67-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d2a67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2a67-107">Alert, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="d2a67-108">Żąda, aby Host wznowił zadanie reprezentowane przez bieżące wystąpienie `IHostTask`, więc zadanie można przerwać.</span><span class="sxs-lookup"><span data-stu-id="d2a67-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="d2a67-109">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="d2a67-110">Pobiera poziom priorytetu wątku zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="d2a67-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d2a67-111">Join, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="d2a67-112">Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące wystąpienie `IHostTask`, upłynie określony przedział czasu lub [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d2a67-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="d2a67-113">SetCLRTask, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="d2a67-114">Kojarzy wystąpienie [interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) z bieżącym wystąpieniem `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="d2a67-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d2a67-115">SetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="d2a67-116">Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="d2a67-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d2a67-117">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="d2a67-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="d2a67-118">Żąda, aby Host przeniesieł zadanie reprezentowane przez bieżące wystąpienie `IHostTask` ze stanu wstrzymania do stanu na żywo, w którym można wykonać kod.</span><span class="sxs-lookup"><span data-stu-id="d2a67-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a67-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2a67-119">Remarks</span></span>  
 <span data-ttu-id="d2a67-120">CLR wywołuje metody zdefiniowane przez `IHostTask`, aby uruchomić zadanie, ustawić jego poziom priorytetu wątku i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d2a67-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a67-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2a67-121">Requirements</span></span>  
 <span data-ttu-id="d2a67-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2a67-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a67-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2a67-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2a67-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2a67-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2a67-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a67-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a67-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2a67-126">See also</span></span>

- [<span data-ttu-id="d2a67-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2a67-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d2a67-128">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2a67-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d2a67-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2a67-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="d2a67-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d2a67-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
