---
title: IHostIoCompletionManager::InitializeHostOverlapped — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dea19a13cd2c741a24695b293ae1c8621ad5688
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157673"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="85ff1-102">IHostIoCompletionManager::InitializeHostOverlapped — Metoda</span><span class="sxs-lookup"><span data-stu-id="85ff1-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="85ff1-103">Zapewnia możliwość zainicjowania wszelkie niestandardowe dane do dołączenia do systemu Win32 hosta `OVERLAPPED` strukturę, która jest używana dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="85ff1-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ff1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85ff1-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85ff1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85ff1-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="85ff1-106">[in] Wskaźnik do Win32 `OVERLAPPED` struktury, które mają zostać dołączone do żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="85ff1-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85ff1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85ff1-107">Return Value</span></span>  
  
|<span data-ttu-id="85ff1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85ff1-108">HRESULT</span></span>|<span data-ttu-id="85ff1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="85ff1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85ff1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="85ff1-110">S_OK</span></span>|<span data-ttu-id="85ff1-111">`InitializeHostOverlapped` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="85ff1-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="85ff1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85ff1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85ff1-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="85ff1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85ff1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85ff1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85ff1-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="85ff1-115">The call timed out.</span></span>|  
|<span data-ttu-id="85ff1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85ff1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85ff1-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="85ff1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85ff1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85ff1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85ff1-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="85ff1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85ff1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85ff1-120">E_FAIL</span></span>|<span data-ttu-id="85ff1-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="85ff1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85ff1-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="85ff1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85ff1-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85ff1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="85ff1-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="85ff1-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="85ff1-125">Za mało dostępnej pamięci na przydzielić żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="85ff1-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85ff1-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85ff1-126">Remarks</span></span>  
 <span data-ttu-id="85ff1-127">Platforma Windows funkcji Użyj `OVERLAPPED` struktura do przechowywania stanu dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="85ff1-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="85ff1-128">CLR wywołuje `InitializeHostOverlapped` metody, aby zapewnić możliwość dołączenia niestandardowe dane do hosta `OVERLAPPED` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="85ff1-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85ff1-129">Aby przejść do początku ich bloku danych niestandardowych, hosty należy ustawić przesunięcie do rozmiaru `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="85ff1-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="85ff1-130">Zwracana wartość wynosząca E_OUTOFMEMORY wskazuje, że host nie może zainicjować swoich danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="85ff1-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="85ff1-131">W tym przypadku CLR zgłasza błąd i nie powiedzie się wywołanie.</span><span class="sxs-lookup"><span data-stu-id="85ff1-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85ff1-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85ff1-132">Requirements</span></span>  
 <span data-ttu-id="85ff1-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ff1-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ff1-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85ff1-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85ff1-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85ff1-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85ff1-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ff1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ff1-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85ff1-137">See also</span></span>

- [<span data-ttu-id="85ff1-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="85ff1-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="85ff1-139">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="85ff1-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="85ff1-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="85ff1-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
