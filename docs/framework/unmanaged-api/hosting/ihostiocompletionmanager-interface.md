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
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133849"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="01138-102">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="01138-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="01138-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do współdziałania z portami zakończenia we/wy dostarczonymi przez hosta.</span><span class="sxs-lookup"><span data-stu-id="01138-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01138-104">Metody</span><span class="sxs-lookup"><span data-stu-id="01138-104">Methods</span></span>  
  
|<span data-ttu-id="01138-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01138-105">Method</span></span>|<span data-ttu-id="01138-106">Opis</span><span class="sxs-lookup"><span data-stu-id="01138-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01138-107">Bind, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="01138-108">Tworzy powiązanie dojścia do portu zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="01138-109">CloseIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="01138-110">Zamyka port, który został utworzony przy użyciu wcześniejszego wywołania do `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="01138-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="01138-111">CreateIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="01138-112">Żąda utworzenia przez hosta nowego portu zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="01138-113">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="01138-114">Pobiera liczbę wątków zakończenia we/wy, które nie przetwarzają obecnie żądań.</span><span class="sxs-lookup"><span data-stu-id="01138-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="01138-115">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="01138-116">Pobiera rozmiar danych niestandardowych, które Host zamierza dołączyć do żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="01138-117">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="01138-118">Pobiera maksymalną liczbę wątków, które host może przydzielić do żądań we/wy usługi.</span><span class="sxs-lookup"><span data-stu-id="01138-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="01138-119">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="01138-120">Pobiera minimalną liczbę wątków przemieszczonych przez hosta w celu obsługi żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="01138-121">InitializeHostOverlapped, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="01138-122">Udostępnia hostowi możliwość zainicjowania wszelkich niestandardowych danych dotyczących żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="01138-123">SetCLRIoCompletionManager, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="01138-124">Dostarcza host ze wskaźnikiem interfejsu do wystąpienia [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) zaimplementowanego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="01138-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="01138-125">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="01138-126">Ustawia maksymalną liczbę wątków przynoszących Host do obsługi żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="01138-127">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="01138-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="01138-128">Ustawia minimalną liczbę wątków, które host powinien przydzielić do zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01138-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01138-129">Remarks</span></span>  
 <span data-ttu-id="01138-130">`IHostIoCompletionManager` odpowiada interfejsowi `ICLRIoCompletionManager` zaimplementowanym przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="01138-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="01138-131">Środowisko CLR wywołuje metody `IHostIoCompletionManager`, aby powiązać dojścia do portów dostarczanych przez hosta, a host wywołuje metody `ICLRIoCompletionManager`, aby raportować ukończenie żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="01138-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01138-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01138-132">Requirements</span></span>  
 <span data-ttu-id="01138-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01138-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01138-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01138-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01138-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01138-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01138-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01138-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01138-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01138-137">See also</span></span>

- [<span data-ttu-id="01138-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01138-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
