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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23ead080823ace1b091568108af8866dcbca14ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770263"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="6479f-102">ICLRTask2::BeginPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="6479f-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="6479f-103">Nowy wątek opóźnienia przerwać żądań z wynikiem przerwań wątku w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="6479f-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6479f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6479f-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6479f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6479f-105">Return Value</span></span>  
 <span data-ttu-id="6479f-106">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6479f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6479f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6479f-107">HRESULT</span></span>|<span data-ttu-id="6479f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6479f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6479f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6479f-109">S_OK</span></span>|<span data-ttu-id="6479f-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6479f-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="6479f-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6479f-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6479f-112">Metoda została wywołana w wątku, który nie jest bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="6479f-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6479f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6479f-113">Remarks</span></span>  
 <span data-ttu-id="6479f-114">Wywołanie tej metody zwiększa licznik opóźnienie wątku przerwania dla bieżącego wątku za pomocą jednej.</span><span class="sxs-lookup"><span data-stu-id="6479f-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="6479f-115">Wywołania `BeginPreventAsyncAbort` i [iclrtask2::endpreventasyncabort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="6479f-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="6479f-116">Tak długo, jak długo wartość licznika jest większa od zera, opóźnienia przerwania wątku dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="6479f-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="6479f-117">Jeśli to wywołanie nie jest sparowana z wywołaniem `EndPreventAsyncAbort` metody jest możliwe osiągnąć stan, w który wątek przerwań nie można dostarczyć do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="6479f-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="6479f-118">Opóźnienie nie jest uznawane wątku, który przerywa sam.</span><span class="sxs-lookup"><span data-stu-id="6479f-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="6479f-119">Funkcje, które jest uwidaczniany przez ta funkcja jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="6479f-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="6479f-120">Niewłaściwe korzystanie z tych metod może spowodować nieokreślone zachowanie na maszynie wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6479f-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="6479f-121">Na przykład, wywołanie `EndPreventAsyncAbort` bez wywoływania pierwszy `BeginPreventAsyncAbort` można ustawić licznik na zero, gdy maszyna wirtualna wcześniej jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="6479f-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="6479f-122">Podobnie Licznik wewnętrzny nie jest sprawdzane pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="6479f-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="6479f-123">Jeśli przekracza całkowity limit, ponieważ jest zwiększany zarówno przez host i maszyna wirtualna, wynikowe zachowanie jest nieokreślone.</span><span class="sxs-lookup"><span data-stu-id="6479f-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6479f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6479f-124">Requirements</span></span>  
 <span data-ttu-id="6479f-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6479f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6479f-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6479f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6479f-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6479f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6479f-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6479f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6479f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6479f-129">See also</span></span>

- [<span data-ttu-id="6479f-130">EndPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="6479f-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="6479f-131">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479f-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="6479f-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479f-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6479f-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479f-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6479f-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479f-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="6479f-135">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6479f-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
