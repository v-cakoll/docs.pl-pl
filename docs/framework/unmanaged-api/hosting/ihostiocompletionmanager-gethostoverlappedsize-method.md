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
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439609"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="810f0-102">IHostIoCompletionManager::GetHostOverlappedSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="810f0-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="810f0-103">Pobiera rozmiar niestandardowych danych, aby dołączyć do żądania operacji We/Wy przez hosta.</span><span class="sxs-lookup"><span data-stu-id="810f0-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="810f0-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="810f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="810f0-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="810f0-106">[out] Wskaźnik do liczba bajtów, które środowisko uruchomieniowe języka wspólnego (CLR) należy przydzielić oprócz rozmiaru Win32 `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="810f0-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="810f0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="810f0-107">Return Value</span></span>  
  
|<span data-ttu-id="810f0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="810f0-108">HRESULT</span></span>|<span data-ttu-id="810f0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="810f0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="810f0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="810f0-110">S_OK</span></span>|<span data-ttu-id="810f0-111">`GetHostOverlappedSize` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="810f0-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="810f0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="810f0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="810f0-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="810f0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="810f0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="810f0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="810f0-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="810f0-115">The call timed out.</span></span>|  
|<span data-ttu-id="810f0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="810f0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="810f0-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="810f0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="810f0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="810f0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="810f0-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="810f0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="810f0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="810f0-120">E_FAIL</span></span>|<span data-ttu-id="810f0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="810f0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="810f0-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="810f0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="810f0-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="810f0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810f0-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="810f0-124">Remarks</span></span>  
 <span data-ttu-id="810f0-125">Wszystkie wywołania asynchroniczne We/Wy do interfejsów API platformy Windows zająć Win32 `OVERLAPPED` obiektu, który zawiera informacje, takie jak pozycję wskaźnika pliku.</span><span class="sxs-lookup"><span data-stu-id="810f0-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="810f0-126">Aby zachować stan, aplikacje, które zwykle wywołania asynchroniczne We/Wy dodać niestandardowe dane do struktury.</span><span class="sxs-lookup"><span data-stu-id="810f0-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="810f0-127">`GetHostOverlappedSize` i [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) możliwość hosta na obejmują takie dane niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="810f0-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="810f0-128">Wywołania CLR `GetHostOverlappedSize` metodę, aby określić rozmiar danych niestandardowych, która hosta można dołączyć do `OVERLAPPED` obiektu.</span><span class="sxs-lookup"><span data-stu-id="810f0-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="810f0-129">`GetHostOverlappedSize` zostanie wywołana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="810f0-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="810f0-130">Niestandardowe dane hosta musi mieć taki sam rozmiar dla każdego żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="810f0-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="810f0-131">Rozmiar `OVERLAPPED` sam obiekt nie znajduje się w wartości `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="810f0-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="810f0-132">Aby uzyskać więcej informacji na temat `OVERLAPPED` struktury, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="810f0-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810f0-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="810f0-133">Requirements</span></span>  
 <span data-ttu-id="810f0-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="810f0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="810f0-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="810f0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="810f0-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="810f0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="810f0-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="810f0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810f0-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="810f0-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="810f0-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="810f0-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="810f0-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="810f0-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
