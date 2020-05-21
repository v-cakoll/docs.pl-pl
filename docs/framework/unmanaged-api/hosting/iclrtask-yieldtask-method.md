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
ms.openlocfilehash: ccfca2f685a88f5802dd58667fbf1fac14727c88
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762906"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="793f1-102">ICLRTask::YieldTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="793f1-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="793f1-103">Żąda, aby środowisko uruchomieniowe języka wspólnego (CLR) odnotuje zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](iclrtask-interface.md) , i udostępnić czas procesora innym zadaniom.</span><span class="sxs-lookup"><span data-stu-id="793f1-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="793f1-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="793f1-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="793f1-105">Return Value</span></span>  
  
|<span data-ttu-id="793f1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="793f1-106">HRESULT</span></span>|<span data-ttu-id="793f1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="793f1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="793f1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="793f1-108">S_OK</span></span>|<span data-ttu-id="793f1-109">`YieldTask`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="793f1-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="793f1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="793f1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="793f1-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="793f1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="793f1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="793f1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="793f1-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="793f1-113">The call timed out.</span></span>|  
|<span data-ttu-id="793f1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="793f1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="793f1-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="793f1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="793f1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="793f1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="793f1-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="793f1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="793f1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="793f1-118">E_FAIL</span></span>|<span data-ttu-id="793f1-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="793f1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="793f1-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="793f1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="793f1-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="793f1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="793f1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="793f1-122">Remarks</span></span>  
 <span data-ttu-id="793f1-123">Host wywołuje `YieldTask` żądania zasobów procesora dla innych zadań lub procesów.</span><span class="sxs-lookup"><span data-stu-id="793f1-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="793f1-124">Ta metoda jest przeznaczona głównie do zezwalania na długotrwały kod w celu zapewnienia czasu procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="793f1-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="793f1-125">Środowisko uruchomieniowe próbuje wykonać zadanie, które jest `ICLRTask` reprezentowane przez bieżące wystąpienie w stanie, w którym może on dać czas przetwarzania, ale nie gwarantuje sukcesu.</span><span class="sxs-lookup"><span data-stu-id="793f1-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="793f1-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="793f1-126">Requirements</span></span>  
 <span data-ttu-id="793f1-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="793f1-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="793f1-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="793f1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="793f1-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="793f1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="793f1-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="793f1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793f1-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="793f1-131">See also</span></span>

- [<span data-ttu-id="793f1-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="793f1-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="793f1-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="793f1-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="793f1-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="793f1-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="793f1-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="793f1-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
