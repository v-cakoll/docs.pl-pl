---
title: IHostSyncManager::CreateRWLockReaderEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: 64cf6c80ab1cf4b3ca52c60d6e72b54c438f9f4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195840"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="261ed-102">IHostSyncManager::CreateRWLockReaderEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="261ed-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="261ed-103">Tworzy obiekt zdarzenia resetowania ręcznego dla implementacji blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="261ed-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="261ed-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="261ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="261ed-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="261ed-106">[in] `true`, jeśli `ppEvent` powinien być zasygnalizowani; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="261ed-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="261ed-107">podczas Plik cookie do skojarzenia z blokadą czytnika.</span><span class="sxs-lookup"><span data-stu-id="261ed-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="261ed-108">określoną Wskaźnik do adresu wystąpienia [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="261ed-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="261ed-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="261ed-109">Return Value</span></span>  
  
|<span data-ttu-id="261ed-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="261ed-110">HRESULT</span></span>|<span data-ttu-id="261ed-111">Opis</span><span class="sxs-lookup"><span data-stu-id="261ed-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="261ed-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="261ed-112">S_OK</span></span>|<span data-ttu-id="261ed-113">`CreateRWLockReaderEvent` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="261ed-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="261ed-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="261ed-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="261ed-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="261ed-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="261ed-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="261ed-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="261ed-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="261ed-117">The call timed out.</span></span>|  
|<span data-ttu-id="261ed-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="261ed-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="261ed-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="261ed-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="261ed-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="261ed-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="261ed-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="261ed-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="261ed-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="261ed-122">E_FAIL</span></span>|<span data-ttu-id="261ed-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="261ed-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="261ed-124">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="261ed-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="261ed-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="261ed-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="261ed-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="261ed-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="261ed-127">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="261ed-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="261ed-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="261ed-128">Remarks</span></span>  
 <span data-ttu-id="261ed-129">Wywołania CLR `CreateRWLockReaderEvent`, aby uzyskać odwołanie do wystąpienia `IHostManualEvent`, które ma być używane w jego implementacji blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="261ed-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="261ed-130">Host może użyć pliku cookie, aby określić, które zadania oczekują na blokadę czytnika przez wykonanie zapytania dotyczącego interfejsu [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="261ed-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="261ed-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="261ed-131">Requirements</span></span>  
 <span data-ttu-id="261ed-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="261ed-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="261ed-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="261ed-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="261ed-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="261ed-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="261ed-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="261ed-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261ed-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="261ed-136">See also</span></span>

- [<span data-ttu-id="261ed-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="261ed-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="261ed-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="261ed-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="261ed-139">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="261ed-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="261ed-140">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="261ed-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
