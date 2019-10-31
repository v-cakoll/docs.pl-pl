---
title: IHostIoCompletionManager::CreateIoCompletionPort — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: c3fa8aeebe529564c0ecc4a970f586fffc97ee05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133881"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="976c5-102">IHostIoCompletionManager::CreateIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="976c5-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="976c5-103">Żąda utworzenia przez hosta nowego portu zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="976c5-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="976c5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="976c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="976c5-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="976c5-106">określoną Wskaźnik do dojścia do nowo utworzonego portu ukończenia we/wy lub 0 (zero), jeśli nie można utworzyć portu.</span><span class="sxs-lookup"><span data-stu-id="976c5-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="976c5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="976c5-107">Return Value</span></span>  
  
|<span data-ttu-id="976c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="976c5-108">HRESULT</span></span>|<span data-ttu-id="976c5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="976c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="976c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="976c5-110">S_OK</span></span>|<span data-ttu-id="976c5-111">`CreateIoCompletionPort` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="976c5-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="976c5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="976c5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="976c5-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="976c5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="976c5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="976c5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="976c5-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="976c5-115">The call timed out.</span></span>|  
|<span data-ttu-id="976c5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="976c5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="976c5-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="976c5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="976c5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="976c5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="976c5-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="976c5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="976c5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="976c5-120">E_FAIL</span></span>|<span data-ttu-id="976c5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="976c5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="976c5-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="976c5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="976c5-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="976c5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="976c5-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="976c5-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="976c5-125">Za mało dostępnej pamięci, aby przydzielić żądany zasób.</span><span class="sxs-lookup"><span data-stu-id="976c5-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="976c5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="976c5-126">Remarks</span></span>  
 <span data-ttu-id="976c5-127">Środowisko CLR wywołuje metodę `CreateIoCompletionPort`, aby zażądać, aby Host utworzył nowy port zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="976c5-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="976c5-128">Wiąże operacje we/wy z tym portem za pomocą wywołania metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="976c5-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="976c5-129">Host raportuje stan z powrotem do środowiska CLR przez wywołanie [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="976c5-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="976c5-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="976c5-130">Requirements</span></span>  
 <span data-ttu-id="976c5-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="976c5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="976c5-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="976c5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="976c5-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="976c5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="976c5-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="976c5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976c5-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="976c5-135">See also</span></span>

- [<span data-ttu-id="976c5-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="976c5-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="976c5-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="976c5-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
