---
title: "IHostIoCompletionManager::InitializeHostOverlapped — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.InitializeHostOverlapped
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b558d638e598ba6e3d0055e3a842976896e99d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="1d639-102">IHostIoCompletionManager::InitializeHostOverlapped — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d639-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="1d639-103">Zapewnia możliwość zainicjować wszelkie niestandardowe dane mają zostać dołączone do systemu Win32 hosta `OVERLAPPED` struktury, która jest używana dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="1d639-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d639-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d639-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d639-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d639-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="1d639-106">[in] Wskaźnik do środowiska Win32 `OVERLAPPED` struktury, które zostaną dołączone do żądania operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="1d639-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d639-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d639-107">Return Value</span></span>  
  
|<span data-ttu-id="1d639-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d639-108">HRESULT</span></span>|<span data-ttu-id="1d639-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1d639-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d639-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d639-110">S_OK</span></span>|<span data-ttu-id="1d639-111">`InitializeHostOverlapped`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1d639-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="1d639-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d639-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d639-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d639-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d639-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d639-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d639-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d639-115">The call timed out.</span></span>|  
|<span data-ttu-id="1d639-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d639-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d639-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1d639-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d639-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d639-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d639-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1d639-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d639-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d639-120">E_FAIL</span></span>|<span data-ttu-id="1d639-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1d639-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d639-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1d639-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d639-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d639-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1d639-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1d639-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1d639-125">Za mało pamięci nie była dostępna do przydzielenia do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1d639-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d639-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d639-126">Remarks</span></span>  
 <span data-ttu-id="1d639-127">Użyj funkcji platformy Windows `OVERLAPPED` struktury do przechowywania stanu dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="1d639-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="1d639-128">Wywołania CLR `InitializeHostOverlapped` metody daje możliwość dołączenia danych niestandardowych do hosta `OVERLAPPED` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1d639-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d639-129">Aby uzyskać na początku bloku ich danych niestandardowych, hosty ustawić przesunięcie rozmiar `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="1d639-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="1d639-130">Zwracana wartość E_OUTOFMEMORY wskazuje, że host nie może zainicjować swoich danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1d639-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="1d639-131">W takim przypadku CLR zgłasza błąd i nie powiodło się wywołanie.</span><span class="sxs-lookup"><span data-stu-id="1d639-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d639-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d639-132">Requirements</span></span>  
 <span data-ttu-id="1d639-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d639-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d639-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d639-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d639-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d639-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d639-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d639-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d639-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d639-137">See Also</span></span>  
 [<span data-ttu-id="1d639-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d639-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="1d639-139">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="1d639-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="1d639-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d639-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
