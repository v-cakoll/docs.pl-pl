---
title: "IHostIoCompletionManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 847d4c3aa3e3da94b4aac4679ada047577379f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="655cf-102">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="655cf-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="655cf-103">Udostępnia metody umożliwiające środowisko uruchomieniowe języka wspólnego (CLR) do interakcji z portów We/Wy dostarczone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="655cf-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="655cf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="655cf-104">Methods</span></span>  
  
|<span data-ttu-id="655cf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-105">Method</span></span>|<span data-ttu-id="655cf-106">Opis</span><span class="sxs-lookup"><span data-stu-id="655cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="655cf-107">BIND — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="655cf-108">Wiąże dojścia do portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="655cf-109">CloseIoCompletionPort — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="655cf-110">Zamyka port, który został utworzony za pomocą wcześniejszych wywołania do `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="655cf-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="655cf-111">CreateIoCompletionPort — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="655cf-112">Żądania, hosta utworzyć nowego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="655cf-113">GetAvailableThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="655cf-114">Pobiera liczbę wątków zakończenia We/Wy, które nie są aktualnie przetwarza żądania.</span><span class="sxs-lookup"><span data-stu-id="655cf-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="655cf-115">GetHostOverlappedSize — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="655cf-116">Pobiera rozmiar niestandardowych danych, aby dołączyć do żądania operacji We/Wy przez hosta.</span><span class="sxs-lookup"><span data-stu-id="655cf-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="655cf-117">GetMaxThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="655cf-118">Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="655cf-119">GetMinThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="655cf-120">Pobiera minimalną liczbę wątków, które zapewnia hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="655cf-121">InitializeHostOverlapped — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="655cf-122">Zapewnia możliwość zainicjować wszelkie niestandardowe dane o żądaniu we/wy hosta.</span><span class="sxs-lookup"><span data-stu-id="655cf-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="655cf-123">SetCLRIoCompletionManager — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="655cf-124">Udostępnia wskaźnik interfejsu do hosta [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia zaimplementowana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="655cf-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="655cf-125">SetMaxThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="655cf-126">Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="655cf-127">SetMinThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="655cf-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="655cf-128">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655cf-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="655cf-129">Remarks</span></span>  
 <span data-ttu-id="655cf-130">`IHostIoCompletionManager`odpowiada `ICLRIoCompletionManager` interfejsu zaimplementowanego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="655cf-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="655cf-131">Środowisko CLR wywołuje metody `IHostIoCompletionManager` można powiązać dojścia do portów, które zapewnia hosta, a host wywołuje metody `ICLRIoCompletionManager` zgłoszenia ukończenia żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="655cf-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="655cf-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="655cf-132">Requirements</span></span>  
 <span data-ttu-id="655cf-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="655cf-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="655cf-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="655cf-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="655cf-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="655cf-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="655cf-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="655cf-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655cf-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="655cf-137">See Also</span></span>  
 [<span data-ttu-id="655cf-138">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="655cf-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
