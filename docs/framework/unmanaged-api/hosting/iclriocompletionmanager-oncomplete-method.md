---
title: ICLRIoCompletionManager::OnComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: b44a71137e39130bb0fe4c303fdff62c76d38cbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141012"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="8f76d-102">ICLRIoCompletionManager::OnComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f76d-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="8f76d-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8f76d-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f76d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f76d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f76d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f76d-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="8f76d-106">podczas Wartość HRESULT wskazująca stan operacji wiązania.</span><span class="sxs-lookup"><span data-stu-id="8f76d-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="8f76d-107">S_OK wskazuje, że operacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f76d-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="8f76d-108">HOST_E_INTERRUPTED wskazuje, że wywołanie zostało przerwane przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="8f76d-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="8f76d-109">E_FAIL wskazuje, że wystąpił nieznany, nieodwracalny błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8f76d-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="8f76d-110">podczas Liczba bajtów transferowanych podczas przetwarzania żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="8f76d-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="8f76d-111">podczas Wskaźnik do struktury `OVERLAPPED`, która została przeniesiona do wywołania metody `IHostIoCompletionManager::Bind`.</span><span class="sxs-lookup"><span data-stu-id="8f76d-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f76d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f76d-112">Return Value</span></span>  
  
|<span data-ttu-id="8f76d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f76d-113">HRESULT</span></span>|<span data-ttu-id="8f76d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8f76d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f76d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f76d-115">S_OK</span></span>|<span data-ttu-id="8f76d-116">`OnComplete` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8f76d-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="8f76d-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f76d-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f76d-118">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f76d-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f76d-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f76d-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f76d-120">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8f76d-120">The call timed out.</span></span>|  
|<span data-ttu-id="8f76d-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f76d-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f76d-122">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8f76d-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f76d-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f76d-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f76d-124">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8f76d-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f76d-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f76d-125">E_FAIL</span></span>|<span data-ttu-id="8f76d-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8f76d-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f76d-127">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="8f76d-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f76d-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f76d-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f76d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f76d-129">Remarks</span></span>  
 <span data-ttu-id="8f76d-130">Jeśli Host implementuje abstrakcję ukończenia operacji we/wy, środowisko CLR wykonuje żądania we/wy za pośrednictwem hosta przy użyciu metod [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8f76d-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="8f76d-131">Następnie Host wywołuje metodę `OnComplete`, aby powiadomić środowisko uruchomieniowe o wyniku takich żądań.</span><span class="sxs-lookup"><span data-stu-id="8f76d-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f76d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f76d-132">Requirements</span></span>  
 <span data-ttu-id="8f76d-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f76d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f76d-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f76d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f76d-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f76d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f76d-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f76d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f76d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f76d-137">See also</span></span>

- [<span data-ttu-id="8f76d-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f76d-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8f76d-139">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f76d-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="8f76d-140">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f76d-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
