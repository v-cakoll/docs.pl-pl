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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cacc96d66d5d4eb46c08c93d9c2793282627539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438236"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="9ac60-102">ICLRTask2::EndPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ac60-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="9ac60-103">Zezwala na nowe lub oczekujące żądania przerwania wątku w wątku przerywa w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="9ac60-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ac60-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9ac60-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ac60-105">Return Value</span></span>  
 <span data-ttu-id="9ac60-106">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9ac60-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ac60-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ac60-107">HRESULT</span></span>|<span data-ttu-id="9ac60-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9ac60-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ac60-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ac60-109">S_OK</span></span>|<span data-ttu-id="9ac60-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9ac60-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="9ac60-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9ac60-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9ac60-112">Metoda została wywołana w wątku, który nie jest bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="9ac60-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ac60-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ac60-113">Remarks</span></span>  
 <span data-ttu-id="9ac60-114">Ten licznik zmniejsza przerwania wątku opóźnienie — metoda podczas wywoływania bieżącego wątku o jeden.</span><span class="sxs-lookup"><span data-stu-id="9ac60-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="9ac60-115">Wywołuje się [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) i `EndPreventAsyncAbort` mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="9ac60-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="9ac60-116">Tak długo, jak wartość licznika jest większa niż zero, opóźnienia przerwania wątku dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="9ac60-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="9ac60-117">Funkcje, które jest udostępniane przez tę funkcję jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="9ac60-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="9ac60-118">Nieprawidłowe użycie tych metod może spowodować nieokreślony zachowanie w maszynie Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9ac60-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="9ac60-119">Na przykład wywołanie elementu `EndPreventAsyncAbort` bez wywoływania pierwszego elementu `BeginPreventAsyncAbort` można ustawić licznik do zera, gdy maszyna wirtualna wcześniej ma zwiększany.</span><span class="sxs-lookup"><span data-stu-id="9ac60-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="9ac60-120">Podobnie wewnętrzny licznik nie jest sprawdzany pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="9ac60-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="9ac60-121">W razie przekroczenia limitu całkowitej, ponieważ jest zwiększany przez hosta i maszyny Wirtualnej, efekty jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="9ac60-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac60-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ac60-122">Requirements</span></span>  
 <span data-ttu-id="9ac60-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac60-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac60-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ac60-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ac60-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ac60-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ac60-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac60-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac60-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ac60-127">See Also</span></span>  
 [<span data-ttu-id="9ac60-128">BeginPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="9ac60-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)  
 [<span data-ttu-id="9ac60-129">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ac60-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="9ac60-130">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ac60-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9ac60-131">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ac60-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9ac60-132">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ac60-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="9ac60-133">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9ac60-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
