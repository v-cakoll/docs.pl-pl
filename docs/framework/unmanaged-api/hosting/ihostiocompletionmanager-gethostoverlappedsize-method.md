---
title: IHostIoCompletionManager::GetHostOverlappedSize — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: a97009a4ebc834d867dddcc350033c550364ea42
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804749"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="99b1b-102">IHostIoCompletionManager::GetHostOverlappedSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="99b1b-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="99b1b-103">Pobiera rozmiar danych niestandardowych, które Host zamierza dołączyć do żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="99b1b-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99b1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99b1b-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="99b1b-106">określoną Wskaźnik do liczby bajtów, które powinny być przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR) oprócz rozmiaru `OVERLAPPED` obiektu Win32.</span><span class="sxs-lookup"><span data-stu-id="99b1b-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99b1b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99b1b-107">Return Value</span></span>  
  
|<span data-ttu-id="99b1b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99b1b-108">HRESULT</span></span>|<span data-ttu-id="99b1b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="99b1b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99b1b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99b1b-110">S_OK</span></span>|<span data-ttu-id="99b1b-111">`GetHostOverlappedSize`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="99b1b-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="99b1b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99b1b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99b1b-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="99b1b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99b1b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99b1b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99b1b-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="99b1b-115">The call timed out.</span></span>|  
|<span data-ttu-id="99b1b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99b1b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99b1b-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="99b1b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99b1b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99b1b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99b1b-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="99b1b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99b1b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99b1b-120">E_FAIL</span></span>|<span data-ttu-id="99b1b-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="99b1b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99b1b-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="99b1b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99b1b-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="99b1b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99b1b-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99b1b-124">Remarks</span></span>  
 <span data-ttu-id="99b1b-125">Wszystkie asynchroniczne wywołania we/wy do interfejsów API platformy Windows przyjmują `OVERLAPPED` obiekt Win32, który zawiera informacje, takie jak położenie wskaźnika pliku.</span><span class="sxs-lookup"><span data-stu-id="99b1b-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="99b1b-126">W celu utrzymania stanu aplikacje, które powodują asynchroniczne wywołania we/wy zwykle dodają niestandardowe dane do struktury.</span><span class="sxs-lookup"><span data-stu-id="99b1b-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="99b1b-127">`GetHostOverlappedSize`i [IHostIoCompletionManager:: InitializeHostOverlapped —](ihostiocompletionmanager-initializehostoverlapped-method.md) umożliwiają hostowi uwzględnienie takich danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="99b1b-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="99b1b-128">Środowisko CLR wywołuje `GetHostOverlappedSize` metodę w celu określenia rozmiaru danych niestandardowych, które Host zamierza dołączyć do `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="99b1b-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99b1b-129">`GetHostOverlappedSize`jest wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="99b1b-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="99b1b-130">Dane niestandardowe hosta muszą mieć taki sam rozmiar dla każdego żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="99b1b-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="99b1b-131">Rozmiar `OVERLAPPED` samego obiektu nie jest uwzględniony w wartości `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="99b1b-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="99b1b-132">Więcej informacji o `OVERLAPPED` strukturze znajduje się w dokumentacji platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="99b1b-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99b1b-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99b1b-133">Requirements</span></span>  
 <span data-ttu-id="99b1b-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99b1b-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b1b-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99b1b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99b1b-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99b1b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99b1b-137">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b1b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b1b-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99b1b-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="99b1b-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="99b1b-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="99b1b-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="99b1b-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
