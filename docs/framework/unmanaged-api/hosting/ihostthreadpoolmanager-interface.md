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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e7976740a79efda8e5ab569f2efb55444012c5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220373"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="1b0b3-102">IHostThreadPoolManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1b0b3-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="1b0b3-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby skonfigurować puli wątków i kolejki elementów roboczych w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b0b3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b0b3-104">Methods</span></span>  
  
|<span data-ttu-id="1b0b3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-105">Method</span></span>|<span data-ttu-id="1b0b3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1b0b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b0b3-107">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="1b0b3-108">Pobiera liczbę wątków w puli wątków, które nie są obecnie przetwarza elementy robocze.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="1b0b3-109">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="1b0b3-110">Pobiera maksymalną liczbę wątków, które przechowuje hosta jednocześnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="1b0b3-111">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="1b0b3-112">Pobiera minimalna liczba bezczynnych wątków, które przechowuje hosta w oczekiwaniu żądań.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="1b0b3-113">QueueUserWorkItem, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="1b0b3-114">Kolejki funkcję do wykonania i zapewnia obiekt zawierający dane do użycia przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="1b0b3-115">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="1b0b3-116">Ustawia maksymalną liczbę wątków, zapewniające przez hosta w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="1b0b3-117">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="1b0b3-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="1b0b3-118">Ustawia minimalna liczba bezczynnych wątków, które hosta, musisz utrzymywać w oczekiwaniu żądań.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b0b3-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b0b3-119">Remarks</span></span>  
 <span data-ttu-id="1b0b3-120">Host nie jest wymagana do skonfigurowania puli wątków przy użyciu wartości określone w wywołaniach `SetMaxThreads` i `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="1b0b3-121">W tym przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.</span><span class="sxs-lookup"><span data-stu-id="1b0b3-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b0b3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b0b3-122">Requirements</span></span>  
 <span data-ttu-id="1b0b3-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b0b3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0b3-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b0b3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b0b3-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b0b3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1b0b3-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1b0b3-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b0b3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b0b3-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="1b0b3-128">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1b0b3-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
