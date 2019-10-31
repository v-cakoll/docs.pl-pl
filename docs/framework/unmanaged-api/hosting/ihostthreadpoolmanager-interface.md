---
title: IHostThreadPoolManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122086"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="2d3cc-102">IHostThreadPoolManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d3cc-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="2d3cc-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do konfigurowania puli wątków i umieszczania elementów roboczych w kolejce w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d3cc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d3cc-104">Methods</span></span>  
  
|<span data-ttu-id="2d3cc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-105">Method</span></span>|<span data-ttu-id="2d3cc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2d3cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d3cc-107">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="2d3cc-108">Pobiera liczbę wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="2d3cc-109">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="2d3cc-110">Pobiera maksymalną liczbę wątków, które Host przechowuje współbieżnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="2d3cc-111">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="2d3cc-112">Pobiera minimalną liczbę bezczynnych wątków hostowanych przez hosta w oczekiwaniu na żądania.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="2d3cc-113">QueueUserWorkItem, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="2d3cc-114">Kolejkuje funkcję do wykonania i dostarcza obiekt zawierający dane, które mają być używane przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="2d3cc-115">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="2d3cc-116">Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="2d3cc-117">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2d3cc-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="2d3cc-118">Określa minimalną liczbę bezczynnych wątków, które host musi zachować w oczekiwaniu na żądania.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d3cc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d3cc-119">Remarks</span></span>  
 <span data-ttu-id="2d3cc-120">Host nie jest wymagany do skonfigurowania puli wątków przy użyciu wartości określonych w wywołaniach metod `SetMaxThreads` i `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="2d3cc-121">W takim przypadku host powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.</span><span class="sxs-lookup"><span data-stu-id="2d3cc-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d3cc-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d3cc-122">Requirements</span></span>  
 <span data-ttu-id="2d3cc-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d3cc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d3cc-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d3cc-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d3cc-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d3cc-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d3cc-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d3cc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3cc-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d3cc-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="2d3cc-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d3cc-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
