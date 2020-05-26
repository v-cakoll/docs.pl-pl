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
ms.openlocfilehash: 90675d9be71342efa903767abbf63102b40a2c35
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804687"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="63d15-102">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63d15-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="63d15-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do współdziałania z portami zakończenia we/wy dostarczonymi przez hosta.</span><span class="sxs-lookup"><span data-stu-id="63d15-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63d15-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63d15-104">Methods</span></span>  
  
|<span data-ttu-id="63d15-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-105">Method</span></span>|<span data-ttu-id="63d15-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63d15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63d15-107">Bind, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="63d15-108">Tworzy powiązanie dojścia do portu zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="63d15-109">CloseIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="63d15-110">Zamyka port, który został utworzony za pomocą wcześniejszego wywołania do `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="63d15-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="63d15-111">CreateIoCompletionPort, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="63d15-112">Żąda utworzenia przez hosta nowego portu zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="63d15-113">GetAvailableThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="63d15-114">Pobiera liczbę wątków zakończenia we/wy, które nie przetwarzają obecnie żądań.</span><span class="sxs-lookup"><span data-stu-id="63d15-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="63d15-115">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="63d15-116">Pobiera rozmiar danych niestandardowych, które Host zamierza dołączyć do żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="63d15-117">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="63d15-118">Pobiera maksymalną liczbę wątków, które host może przydzielić do żądań we/wy usługi.</span><span class="sxs-lookup"><span data-stu-id="63d15-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="63d15-119">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="63d15-120">Pobiera minimalną liczbę wątków przemieszczonych przez hosta w celu obsługi żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="63d15-121">InitializeHostOverlapped, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="63d15-122">Udostępnia hostowi możliwość zainicjowania wszelkich niestandardowych danych dotyczących żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="63d15-123">SetCLRIoCompletionManager, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="63d15-124">Dostarcza host ze wskaźnikiem interfejsu do wystąpienia [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) zaimplementowanego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="63d15-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="63d15-125">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="63d15-126">Ustawia maksymalną liczbę wątków przynoszących Host do obsługi żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="63d15-127">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63d15-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="63d15-128">Ustawia minimalną liczbę wątków, które host powinien przydzielić do zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63d15-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63d15-129">Remarks</span></span>  
 <span data-ttu-id="63d15-130">`IHostIoCompletionManager`odnosi się do `ICLRIoCompletionManager` interfejsu implementowanego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="63d15-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="63d15-131">Środowisko CLR wywołuje metody `IHostIoCompletionManager` w celu powiązania dojść z portami dostarczanymi przez hosta, a host wywołuje metody `ICLRIoCompletionManager` w celu zgłaszania ukończenia żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="63d15-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63d15-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63d15-132">Requirements</span></span>  
 <span data-ttu-id="63d15-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63d15-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d15-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63d15-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63d15-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63d15-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63d15-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d15-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d15-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63d15-137">See also</span></span>

- [<span data-ttu-id="63d15-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63d15-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
