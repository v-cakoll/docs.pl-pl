---
title: ICLRTask2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172474"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="c7929-102">ICLRTask2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7929-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="c7929-103">Oferuje wszystkie funkcje [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu; ponadto udostępnia metody, które umożliwiają wątku przerywa opóźnionych w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c7929-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7929-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7929-104">Methods</span></span>  
  
|<span data-ttu-id="c7929-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7929-105">Method</span></span>|<span data-ttu-id="c7929-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7929-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7929-107">BeginPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="c7929-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="c7929-108">Nowy wątek opóźnienia przerwać żądania w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c7929-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="c7929-109">EndPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="c7929-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="c7929-110">Zezwala na nowe lub oczekujące żądania przerwania wątku spowoduje w wątku przerywa w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c7929-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7929-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7929-111">Remarks</span></span>  
 <span data-ttu-id="c7929-112">`ICLRTask2` Interfejs dziedziczy `ICLRTask` interfejs i dodaje metody, które umożliwiają hosta opóźnienia przerwań wątku, do ochrony region kodu, które muszą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c7929-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="c7929-113">Wywoływanie `BeginPreventAsyncAbort` zwiększa licznik opóźnienie wątku przerwania dla bieżącego wątku i wywołania `EndPreventAsyncAbort` zmniejsza ją.</span><span class="sxs-lookup"><span data-stu-id="c7929-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="c7929-114">Wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="c7929-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="c7929-115">Tak długo, jak długo wartość licznika jest większa od zera, opóźnienia przerwania wątku dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="c7929-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="c7929-116">Jeśli wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` są nie sparowano istnieje możliwość osiągnąć stan, w który wątek przerwań nie można dostarczyć do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="c7929-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="c7929-117">Opóźnienie nie jest uznawane wątku, który przerywa sam.</span><span class="sxs-lookup"><span data-stu-id="c7929-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="c7929-118">Funkcje, które jest uwidaczniany przez ta funkcja jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="c7929-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="c7929-119">Niewłaściwe korzystanie z tych metod może spowodować nieokreślone zachowanie na maszynie wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c7929-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="c7929-120">Na przykład, wywołanie `EndPreventAsyncAbort` bez wywoływania pierwszy `BeginPreventAsyncAbort` można ustawić licznik na zero, gdy maszyna wirtualna wcześniej jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="c7929-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="c7929-121">Podobnie Licznik wewnętrzny nie jest sprawdzane pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="c7929-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="c7929-122">Jeśli przekracza całkowity limit, ponieważ jest zwiększany zarówno przez host i maszyna wirtualna, wynikowe zachowanie jest nieokreślone.</span><span class="sxs-lookup"><span data-stu-id="c7929-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="c7929-123">Dla informacji na temat elementów członkowskich są dziedziczone z `ICLRTask` i informacje o innych zastosowań tego interfejsu, [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c7929-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7929-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7929-124">Requirements</span></span>  
 <span data-ttu-id="c7929-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7929-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7929-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7929-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7929-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7929-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c7929-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c7929-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7929-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7929-129">See also</span></span>

- [<span data-ttu-id="c7929-130">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7929-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c7929-131">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7929-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c7929-132">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7929-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c7929-133">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7929-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="c7929-134">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c7929-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
