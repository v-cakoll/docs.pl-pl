---
title: "IHostIoCompletionManager::GetHostOverlappedSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetHostOverlappedSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6633e0271f29d44bb1d14495d80ffdf9868485a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="1f461-102">IHostIoCompletionManager::GetHostOverlappedSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f461-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="1f461-103">Pobiera rozmiar niestandardowych danych, aby dołączyć do żądania operacji We/Wy przez hosta.</span><span class="sxs-lookup"><span data-stu-id="1f461-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f461-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f461-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f461-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="1f461-106">[out] Wskaźnik do liczba bajtów, które środowisko uruchomieniowe języka wspólnego (CLR) należy przydzielić oprócz rozmiaru Win32 `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f461-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f461-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f461-107">Return Value</span></span>  
  
|<span data-ttu-id="1f461-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f461-108">HRESULT</span></span>|<span data-ttu-id="1f461-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1f461-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f461-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f461-110">S_OK</span></span>|<span data-ttu-id="1f461-111">`GetHostOverlappedSize`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f461-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="1f461-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f461-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f461-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f461-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f461-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f461-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f461-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f461-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f461-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f461-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f461-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1f461-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f461-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f461-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f461-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1f461-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f461-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f461-120">E_FAIL</span></span>|<span data-ttu-id="1f461-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1f461-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f461-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1f461-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f461-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f461-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f461-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f461-124">Remarks</span></span>  
 <span data-ttu-id="1f461-125">Wszystkie wywołania asynchroniczne We/Wy do interfejsów API platformy Windows zająć Win32 `OVERLAPPED` obiektu, który zawiera informacje, takie jak pozycję wskaźnika pliku.</span><span class="sxs-lookup"><span data-stu-id="1f461-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="1f461-126">Aby zachować stan, aplikacje, które zwykle wywołania asynchroniczne We/Wy dodać niestandardowe dane do struktury.</span><span class="sxs-lookup"><span data-stu-id="1f461-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="1f461-127">`GetHostOverlappedSize`i [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) możliwość hosta na obejmują takie dane niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="1f461-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="1f461-128">Wywołania CLR `GetHostOverlappedSize` metodę, aby określić rozmiar danych niestandardowych, która hosta można dołączyć do `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f461-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f461-129">`GetHostOverlappedSize`zostanie wywołana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1f461-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="1f461-130">Niestandardowe dane hosta musi mieć taki sam rozmiar dla każdego żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="1f461-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f461-131">Rozmiar `OVERLAPPED` sam obiekt nie znajduje się w wartości `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="1f461-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="1f461-132">Aby uzyskać więcej informacji na temat `OVERLAPPED` struktury, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1f461-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f461-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f461-133">Requirements</span></span>  
 <span data-ttu-id="1f461-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f461-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f461-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f461-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f461-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f461-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f461-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f461-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f461-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f461-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="1f461-139">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f461-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="1f461-140">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f461-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
