---
title: "IHostThreadPoolManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1cd58c53deec0a895ae6f67cccf26d2c8c2530be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="5d520-102">IHostThreadPoolManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5d520-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="5d520-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) w celu skonfigurowania puli wątków i kolejki elementów roboczych w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5d520-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d520-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d520-104">Methods</span></span>  
  
|<span data-ttu-id="5d520-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-105">Method</span></span>|<span data-ttu-id="5d520-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5d520-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d520-107">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="5d520-108">Pobiera liczbę wątków w puli wątków, które nie są aktualnie przetwarza elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="5d520-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="5d520-109">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="5d520-110">Pobiera maksymalną liczbę wątków, która jest obsługiwana przez hosta jednocześnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5d520-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="5d520-111">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="5d520-112">Pobiera minimalna liczba wątków bezczynności, która jest obsługiwana przez hosta w oczekiwaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="5d520-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="5d520-113">QueueUserWorkItem, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="5d520-114">Funkcja do wykonania kolejek i udostępnia obiekt zawierający dane, które mają być używane przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="5d520-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="5d520-115">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="5d520-116">Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5d520-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="5d520-117">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5d520-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="5d520-118">Ustawia minimalną liczbę bezczynności wątków, które muszą zachować hosta w oczekiwaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="5d520-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d520-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d520-119">Remarks</span></span>  
 <span data-ttu-id="5d520-120">Host nie jest wymagana do skonfigurowania puli wątków przy użyciu wartości określone w wywołaniach `SetMaxThreads` i `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="5d520-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="5d520-121">W takim przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.</span><span class="sxs-lookup"><span data-stu-id="5d520-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d520-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d520-122">Requirements</span></span>  
 <span data-ttu-id="5d520-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d520-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d520-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d520-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d520-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d520-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d520-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d520-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d520-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d520-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="5d520-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5d520-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
