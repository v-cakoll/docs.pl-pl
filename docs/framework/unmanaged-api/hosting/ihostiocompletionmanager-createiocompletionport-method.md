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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cf7978af4081b84a361e0a96a6c9da7180cb217
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194048"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="abad8-102">IHostIoCompletionManager::CreateIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="abad8-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="abad8-103">Żądania, że host tworzą nowy port wykonywania operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="abad8-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abad8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abad8-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abad8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abad8-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="abad8-106">[out] Wskaźnik do dojścia do nowo utworzonego portu zakończenia We/Wy lub od 0 (zero), jeśli nie można utworzyć portu.</span><span class="sxs-lookup"><span data-stu-id="abad8-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abad8-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="abad8-107">Return Value</span></span>  
  
|<span data-ttu-id="abad8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abad8-108">HRESULT</span></span>|<span data-ttu-id="abad8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="abad8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abad8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="abad8-110">S_OK</span></span>|<span data-ttu-id="abad8-111">`CreateIoCompletionPort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="abad8-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="abad8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abad8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abad8-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="abad8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="abad8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="abad8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="abad8-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="abad8-115">The call timed out.</span></span>|  
|<span data-ttu-id="abad8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="abad8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="abad8-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="abad8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="abad8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="abad8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="abad8-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="abad8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="abad8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="abad8-120">E_FAIL</span></span>|<span data-ttu-id="abad8-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="abad8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="abad8-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="abad8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="abad8-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="abad8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="abad8-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="abad8-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="abad8-125">Za mało dostępnej pamięci na przydzielić żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="abad8-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abad8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abad8-126">Remarks</span></span>  
 <span data-ttu-id="abad8-127">CLR wywołuje `CreateIoCompletionPort` metodę, aby zażądać, że host tworzą nowy port wykonywania operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="abad8-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="abad8-128">Operacje We/Wy jest powiązana z tym portem za pomocą wywołania [ihostiocompletionmanager::BIND —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="abad8-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="abad8-129">Host raportuje stan ją do środowiska CLR przez wywołanie metody [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="abad8-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abad8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abad8-130">Requirements</span></span>  
 <span data-ttu-id="abad8-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abad8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abad8-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abad8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abad8-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abad8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abad8-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abad8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abad8-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abad8-135">See also</span></span>

- [<span data-ttu-id="abad8-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="abad8-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="abad8-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="abad8-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
