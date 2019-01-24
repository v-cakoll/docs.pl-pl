---
title: IHostIoCompletionManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186f5618cce7a70bc4fab55616a0f8b08025a81f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542540"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="60348-102">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="60348-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="60348-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do interakcji z portów We/Wy udostępniane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="60348-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60348-104">Metody</span><span class="sxs-lookup"><span data-stu-id="60348-104">Methods</span></span>  
  
|<span data-ttu-id="60348-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="60348-105">Method</span></span>|<span data-ttu-id="60348-106">Opis</span><span class="sxs-lookup"><span data-stu-id="60348-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60348-107">Bind, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="60348-108">Wiąże dojścia do portu ukończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="60348-109">CloseIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="60348-110">Zamyka port, który został utworzony przy użyciu wcześniejszego wywołania funkcji `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="60348-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="60348-111">CreateIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="60348-112">Żądania, że host tworzą nowy port wykonywania operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="60348-113">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="60348-114">Pobiera liczbę wątków zakończenia operacji We/Wy, które nie są obecnie przetwarza żądania.</span><span class="sxs-lookup"><span data-stu-id="60348-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="60348-115">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="60348-116">Pobiera rozmiar danych niestandardowych, aby dołączyć do żądań We/Wy przez hosta.</span><span class="sxs-lookup"><span data-stu-id="60348-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="60348-117">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="60348-118">Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="60348-119">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="60348-120">Pobiera minimalną liczbę wątków, udostępnianych przez hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="60348-121">InitializeHostOverlapped, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="60348-122">Zapewnia możliwość zainicjowania wszelkie niestandardowe dane dotyczące żądania We/Wy hosta.</span><span class="sxs-lookup"><span data-stu-id="60348-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="60348-123">SetCLRIoCompletionManager, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="60348-124">Udostępnia wskaźnik interfejsu do hosta [iclriocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="60348-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="60348-125">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="60348-126">Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="60348-127">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="60348-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="60348-128">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60348-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60348-129">Remarks</span></span>  
 <span data-ttu-id="60348-130">`IHostIoCompletionManager` odnosi się do `ICLRIoCompletionManager` interfejs implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="60348-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="60348-131">Środowisko CLR wywołuje metody `IHostIoCompletionManager` powiązać porty, które zapewnia hosta, a host wywołuje metody uchwytów `ICLRIoCompletionManager` zgłosić realizacji żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="60348-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60348-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60348-132">Requirements</span></span>  
 <span data-ttu-id="60348-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60348-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60348-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60348-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60348-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60348-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60348-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60348-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60348-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60348-137">See also</span></span>
- [<span data-ttu-id="60348-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="60348-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
