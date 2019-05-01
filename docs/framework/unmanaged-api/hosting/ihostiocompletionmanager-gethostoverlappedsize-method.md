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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4a5661128765cc058417fef6373767d46a4bd7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796906"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="4f597-102">IHostIoCompletionManager::GetHostOverlappedSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f597-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="4f597-103">Pobiera rozmiar danych niestandardowych, aby dołączyć do żądań We/Wy przez hosta.</span><span class="sxs-lookup"><span data-stu-id="4f597-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f597-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f597-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f597-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f597-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="4f597-106">[out] Wskaźnik do liczby bajtów, które środowisko uruchomieniowe języka wspólnego (CLR) należy przydzielić oprócz rozmiaru Win32 `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f597-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f597-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4f597-107">Return Value</span></span>  
  
|<span data-ttu-id="4f597-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f597-108">HRESULT</span></span>|<span data-ttu-id="4f597-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4f597-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f597-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f597-110">S_OK</span></span>|<span data-ttu-id="4f597-111">`GetHostOverlappedSize` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4f597-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="4f597-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f597-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f597-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4f597-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f597-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f597-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f597-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4f597-115">The call timed out.</span></span>|  
|<span data-ttu-id="4f597-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f597-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f597-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4f597-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f597-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f597-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f597-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4f597-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f597-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f597-120">E_FAIL</span></span>|<span data-ttu-id="4f597-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4f597-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f597-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4f597-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f597-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4f597-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f597-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f597-124">Remarks</span></span>  
 <span data-ttu-id="4f597-125">Asynchroniczne wywołania operacji We/Wy do interfejsów API platformy Windows zająć Win32 `OVERLAPPED` obiektu, który zawiera informacje, takie jak pozycja wskaźnika pliku.</span><span class="sxs-lookup"><span data-stu-id="4f597-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="4f597-126">Do zarządzania stanem, aplikacje, które zwykle wywołania asynchroniczne operacje We/Wy, należy dodać niestandardowe dane do struktury.</span><span class="sxs-lookup"><span data-stu-id="4f597-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="4f597-127">`GetHostOverlappedSize` i [ihostiocompletionmanager::initializehostoverlapped —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) zapewnienia możliwości dla hosta, obejmujący takie dane niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="4f597-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="4f597-128">CLR wywołuje `GetHostOverlappedSize` metodę, aby określić rozmiar danych niestandardowych, że host nie chce dołączyć do `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f597-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f597-129">`GetHostOverlappedSize` zostanie wywołana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4f597-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="4f597-130">Niestandardowe dane hosta musi być taki sam rozmiar dla każdego żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="4f597-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f597-131">Rozmiar `OVERLAPPED` sam obiekt nie znajduje się w wartości `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="4f597-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="4f597-132">Aby uzyskać więcej informacji na temat `OVERLAPPED` struktury, można znaleźć w dokumentacji platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="4f597-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f597-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f597-133">Requirements</span></span>  
 <span data-ttu-id="4f597-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f597-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f597-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f597-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f597-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f597-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f597-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f597-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f597-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f597-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="4f597-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f597-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4f597-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f597-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
