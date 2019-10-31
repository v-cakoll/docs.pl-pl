---
title: ICLRTask2::EndPreventAsyncAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124552"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="4ac80-102">ICLRTask2::EndPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ac80-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="4ac80-103">Zezwala na to, aby nowe lub oczekujące żądania przerwania wątku powodowały przerwania wątku w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4ac80-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ac80-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4ac80-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ac80-105">Return Value</span></span>  
 <span data-ttu-id="4ac80-106">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4ac80-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4ac80-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ac80-107">HRESULT</span></span>|<span data-ttu-id="4ac80-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4ac80-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ac80-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ac80-109">S_OK</span></span>|<span data-ttu-id="4ac80-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4ac80-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="4ac80-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4ac80-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4ac80-112">Metoda została wywołana w wątku, który nie jest bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="4ac80-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ac80-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ac80-113">Remarks</span></span>  
 <span data-ttu-id="4ac80-114">Wywołanie tej metody zmniejsza licznik Opóźnij wątek-Abort dla bieżącego wątku o jeden.</span><span class="sxs-lookup"><span data-stu-id="4ac80-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="4ac80-115">Wywołania [ICLRTask2:: BeginPreventAsyncAbort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) i `EndPreventAsyncAbort` mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="4ac80-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="4ac80-116">Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione.</span><span class="sxs-lookup"><span data-stu-id="4ac80-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="4ac80-117">Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="4ac80-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="4ac80-118">Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4ac80-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="4ac80-119">Na przykład wywoływanie `EndPreventAsyncAbort` bez uprzedniego wywołania `BeginPreventAsyncAbort` może spowodować, że licznik ma wartość zero, gdy maszyna wirtualna została wcześniej zwiększona.</span><span class="sxs-lookup"><span data-stu-id="4ac80-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="4ac80-120">Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="4ac80-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="4ac80-121">W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.</span><span class="sxs-lookup"><span data-stu-id="4ac80-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac80-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ac80-122">Requirements</span></span>  
 <span data-ttu-id="4ac80-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ac80-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ac80-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ac80-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ac80-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ac80-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ac80-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ac80-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac80-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ac80-127">See also</span></span>

- [<span data-ttu-id="4ac80-128">BeginPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="4ac80-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="4ac80-129">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac80-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="4ac80-130">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac80-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4ac80-131">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac80-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4ac80-132">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac80-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4ac80-133">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4ac80-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
