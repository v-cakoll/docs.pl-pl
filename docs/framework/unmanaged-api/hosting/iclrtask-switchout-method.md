---
title: ICLRTask::SwitchOut — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 75517ae55ebae07242f19c19c5473780ce4b0809
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762919"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="ce14f-102">ICLRTask::SwitchOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce14f-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="ce14f-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), że zadanie reprezentowane przez bieżące wystąpienie [ICLRTask](iclrtask-interface.md) nie jest już w stanie obsługiwanym.</span><span class="sxs-lookup"><span data-stu-id="ce14f-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce14f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce14f-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ce14f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ce14f-105">Return Value</span></span>  
  
|<span data-ttu-id="ce14f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce14f-106">HRESULT</span></span>|<span data-ttu-id="ce14f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ce14f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce14f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce14f-108">S_OK</span></span>|<span data-ttu-id="ce14f-109">`SwitchOut`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ce14f-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="ce14f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ce14f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce14f-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ce14f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce14f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce14f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce14f-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ce14f-113">The call timed out.</span></span>|  
|<span data-ttu-id="ce14f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce14f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce14f-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ce14f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce14f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce14f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce14f-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ce14f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce14f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce14f-118">E_FAIL</span></span>|<span data-ttu-id="ce14f-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ce14f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce14f-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ce14f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce14f-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ce14f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce14f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce14f-122">Remarks</span></span>  
 <span data-ttu-id="ce14f-123">Host wywołuje `SwitchOut` w celu informowania środowiska CLR o tymczasowym zatrzymaniu wykonywania zadania, które `ICLRTask` reprezentuje bieżące wystąpienie, i ponownie planuje zadanie.</span><span class="sxs-lookup"><span data-stu-id="ce14f-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce14f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce14f-124">Requirements</span></span>  
 <span data-ttu-id="ce14f-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce14f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce14f-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce14f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce14f-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce14f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce14f-128">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce14f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce14f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce14f-129">See also</span></span>

- [<span data-ttu-id="ce14f-130">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ce14f-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ce14f-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce14f-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ce14f-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce14f-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ce14f-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce14f-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
