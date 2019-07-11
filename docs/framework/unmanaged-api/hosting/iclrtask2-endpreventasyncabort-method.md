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
ms.openlocfilehash: 36947eb33460fe3f15cf4ade1cad55cb5e77f1cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770231"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="4b66c-102">ICLRTask2::EndPreventAsyncAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b66c-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="4b66c-103">Zezwala na nowe lub oczekujące żądania przerwania wątku spowoduje w wątku przerywa w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4b66c-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b66c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b66c-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b66c-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b66c-105">Return Value</span></span>  
 <span data-ttu-id="4b66c-106">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4b66c-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4b66c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b66c-107">HRESULT</span></span>|<span data-ttu-id="4b66c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4b66c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b66c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b66c-109">S_OK</span></span>|<span data-ttu-id="4b66c-110">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4b66c-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="4b66c-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4b66c-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4b66c-112">Metoda została wywołana w wątku, który nie jest bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="4b66c-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b66c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b66c-113">Remarks</span></span>  
 <span data-ttu-id="4b66c-114">Wywoływanie ten licznik zmniejsza o jeden przerywania wątku opóźnienie metody dla bieżącego wątku za pomocą jednej.</span><span class="sxs-lookup"><span data-stu-id="4b66c-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="4b66c-115">Wywołania [iclrtask2::beginpreventasyncabort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) i `EndPreventAsyncAbort` mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="4b66c-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="4b66c-116">Tak długo, jak długo wartość licznika jest większa od zera, opóźnienia przerwania wątku dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="4b66c-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="4b66c-117">Funkcje, które jest uwidaczniany przez ta funkcja jest używana wewnętrznie przez maszynę wirtualną (VM).</span><span class="sxs-lookup"><span data-stu-id="4b66c-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="4b66c-118">Niewłaściwe korzystanie z tych metod może spowodować nieokreślone zachowanie na maszynie wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4b66c-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="4b66c-119">Na przykład, wywołanie `EndPreventAsyncAbort` bez wywoływania pierwszy `BeginPreventAsyncAbort` można ustawić licznik na zero, gdy maszyna wirtualna wcześniej jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="4b66c-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="4b66c-120">Podobnie Licznik wewnętrzny nie jest sprawdzane pod kątem przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="4b66c-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="4b66c-121">Jeśli przekracza całkowity limit, ponieważ jest zwiększany zarówno przez host i maszyna wirtualna, wynikowe zachowanie jest nieokreślone.</span><span class="sxs-lookup"><span data-stu-id="4b66c-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b66c-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b66c-122">Requirements</span></span>  
 <span data-ttu-id="4b66c-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b66c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b66c-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b66c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b66c-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b66c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b66c-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b66c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b66c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b66c-127">See also</span></span>

- [<span data-ttu-id="4b66c-128">BeginPreventAsyncAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="4b66c-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="4b66c-129">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b66c-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="4b66c-130">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b66c-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4b66c-131">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b66c-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4b66c-132">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b66c-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4b66c-133">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4b66c-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
