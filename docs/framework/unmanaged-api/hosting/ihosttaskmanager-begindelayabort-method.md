---
title: IHostTaskManager::BeginDelayAbort — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: ea3269d06fdd3f5a2e365465d45ba6e569127b0a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842377"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="baed8-102">IHostTaskManager::BeginDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="baed8-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="baed8-103">Powiadamia hosta, że kod zarządzany wprowadza okres, w którym bieżące zadanie nie może zostać przerwane.</span><span class="sxs-lookup"><span data-stu-id="baed8-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baed8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baed8-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="baed8-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baed8-105">Return Value</span></span>  
  
|<span data-ttu-id="baed8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baed8-106">HRESULT</span></span>|<span data-ttu-id="baed8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="baed8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baed8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="baed8-108">S_OK</span></span>|<span data-ttu-id="baed8-109">`BeginDelayAbort`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="baed8-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="baed8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="baed8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="baed8-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="baed8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="baed8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="baed8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="baed8-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="baed8-113">The call timed out.</span></span>|  
|<span data-ttu-id="baed8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="baed8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="baed8-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="baed8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="baed8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="baed8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="baed8-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="baed8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="baed8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baed8-118">E_FAIL</span></span>|<span data-ttu-id="baed8-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="baed8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="baed8-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="baed8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="baed8-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="baed8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="baed8-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="baed8-122">E_UNEXPECTED</span></span>|<span data-ttu-id="baed8-123">`BeginDelayAbort`został już wywołany, ale odpowiednie wywołanie do [EndDelayAbort —](ihosttaskmanager-enddelayabort-method.md) nie zostało jeszcze odebrane.</span><span class="sxs-lookup"><span data-stu-id="baed8-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baed8-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baed8-124">Remarks</span></span>  
 <span data-ttu-id="baed8-125">Host nie może przerwać bieżącego zadania, dopóki nie `EndDelayAbort` zostanie wywołane.</span><span class="sxs-lookup"><span data-stu-id="baed8-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="baed8-126">Jeśli inne wywołanie `BeginDelayAbort` zostanie wykonane bez wywołania wywołującego do `EndDelayAbort` , host powinien zwrócić E_UNEXPECTED z `BeginDelayAbort` i nie powinien podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="baed8-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baed8-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baed8-127">Requirements</span></span>  
 <span data-ttu-id="baed8-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baed8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baed8-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="baed8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baed8-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="baed8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baed8-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baed8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baed8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baed8-132">See also</span></span>

- [<span data-ttu-id="baed8-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="baed8-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="baed8-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="baed8-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="baed8-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="baed8-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
