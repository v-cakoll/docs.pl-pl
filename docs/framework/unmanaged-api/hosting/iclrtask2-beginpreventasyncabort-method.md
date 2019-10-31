---
title: ICLRTask2::BeginPreventAsyncAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: 67841bbcd796e41b3b81f922020fe6c3677730c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124567"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="d2dc9-102">ICLRTask2::BeginPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2dc9-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="d2dc9-103">Opóźnia nowe żądania przerwania wątku z wyniku przerwania wątku w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2dc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2dc9-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d2dc9-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2dc9-105">Return Value</span></span>  
 <span data-ttu-id="d2dc9-106">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d2dc9-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2dc9-107">HRESULT</span></span>|<span data-ttu-id="d2dc9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d2dc9-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2dc9-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2dc9-109">S_OK</span></span>|<span data-ttu-id="d2dc9-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="d2dc9-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d2dc9-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d2dc9-112">Metoda została wywołana w wątku, który nie jest bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2dc9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2dc9-113">Remarks</span></span>  
 <span data-ttu-id="d2dc9-114">Wywołanie tej metody zwiększa licznik Opóźnij wątek wątku dla bieżącego wątku o jeden.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="d2dc9-115">Wywołania `BeginPreventAsyncAbort` i [ICLRTask2:: EndPreventAsyncAbort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="d2dc9-116">Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="d2dc9-117">Jeśli to wywołanie nie jest sparowane z wywołaniem metody `EndPreventAsyncAbort`, możliwe jest osiągnięcie stanu, w którym przerwania wątku nie można dostarczyć do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="d2dc9-118">Opóźnienie nie jest uznawane za wątek, który przerywa siebie.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="d2dc9-119">Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="d2dc9-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="d2dc9-120">Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="d2dc9-121">Na przykład wywoływanie `EndPreventAsyncAbort` bez uprzedniego wywołania `BeginPreventAsyncAbort` może spowodować, że licznik ma wartość zero, gdy maszyna wirtualna została wcześniej zwiększona.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="d2dc9-122">Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="d2dc9-123">W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.</span><span class="sxs-lookup"><span data-stu-id="d2dc9-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2dc9-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2dc9-124">Requirements</span></span>  
 <span data-ttu-id="d2dc9-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2dc9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2dc9-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2dc9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2dc9-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2dc9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2dc9-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2dc9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dc9-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2dc9-129">See also</span></span>

- [<span data-ttu-id="d2dc9-130">EndPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="d2dc9-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="d2dc9-131">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2dc9-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="d2dc9-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2dc9-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d2dc9-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2dc9-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d2dc9-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2dc9-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="d2dc9-135">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d2dc9-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
