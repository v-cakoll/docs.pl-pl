---
title: "ICLRTask2::BeginPreventAsyncAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.BeginPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33136dfbfa8bb3e0147bc1a1c1bb9e88ab2e4239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="56e3e-102">ICLRTask2::BeginPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="56e3e-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="56e3e-103">Opóźnienia nowego wątku przerwać żądań z wynikiem przerwań wątek w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="56e3e-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56e3e-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56e3e-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56e3e-105">Return Value</span></span>  
 <span data-ttu-id="56e3e-106">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="56e3e-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="56e3e-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56e3e-107">HRESULT</span></span>|<span data-ttu-id="56e3e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="56e3e-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56e3e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="56e3e-109">S_OK</span></span>|<span data-ttu-id="56e3e-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="56e3e-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="56e3e-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="56e3e-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="56e3e-112">Metoda została wywołana w wątku, który nie jest bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="56e3e-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56e3e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56e3e-113">Remarks</span></span>  
 <span data-ttu-id="56e3e-114">Wywołanie tej metody zwiększa licznik opóźnienie wątku przerwania bieżącego wątku o jeden.</span><span class="sxs-lookup"><span data-stu-id="56e3e-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="56e3e-115">Wywołuje się `BeginPreventAsyncAbort` i [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="56e3e-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="56e3e-116">Tak długo, jak wartość licznika jest większa niż zero, opóźnienia przerwania wątku dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="56e3e-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="56e3e-117">Jeśli to wywołanie nie jest sparowana z wywołania `EndPreventAsyncAbort` metody jest możliwość przejścia w wątku, który przerwań nie może zostać dostarczona do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="56e3e-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="56e3e-118">Opóźnienie nie jest honorowana dla wątku, który przerywa samej siebie.</span><span class="sxs-lookup"><span data-stu-id="56e3e-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="56e3e-119">Funkcje, które jest udostępniane przez tę funkcję jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="56e3e-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="56e3e-120">Nieprawidłowe użycie tych metod może spowodować nieokreślony zachowanie w maszynie Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="56e3e-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="56e3e-121">Na przykład wywołanie elementu `EndPreventAsyncAbort` bez wywoływania pierwszego elementu `BeginPreventAsyncAbort` można ustawić licznik do zera, gdy maszyna wirtualna wcześniej ma zwiększany.</span><span class="sxs-lookup"><span data-stu-id="56e3e-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="56e3e-122">Podobnie wewnętrzny licznik nie jest sprawdzany pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="56e3e-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="56e3e-123">W razie przekroczenia limitu całkowitej, ponieważ jest zwiększany przez hosta i maszyny Wirtualnej, efekty jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="56e3e-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e3e-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56e3e-124">Requirements</span></span>  
 <span data-ttu-id="56e3e-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56e3e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e3e-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56e3e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56e3e-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56e3e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56e3e-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56e3e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e3e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56e3e-129">See Also</span></span>  
 [<span data-ttu-id="56e3e-130">EndPreventAsyncAbort — metoda</span><span class="sxs-lookup"><span data-stu-id="56e3e-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [<span data-ttu-id="56e3e-131">ICLRTask2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="56e3e-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="56e3e-132">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="56e3e-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="56e3e-133">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="56e3e-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="56e3e-134">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="56e3e-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="56e3e-135">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="56e3e-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
