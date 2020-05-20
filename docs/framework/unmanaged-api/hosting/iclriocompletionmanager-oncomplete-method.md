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
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703813"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="176a4-102">ICLRIoCompletionManager::OnComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="176a4-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="176a4-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="176a4-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="176a4-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="176a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="176a4-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="176a4-106">podczas Wartość HRESULT wskazująca stan operacji wiązania.</span><span class="sxs-lookup"><span data-stu-id="176a4-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="176a4-107">S_OK wskazuje, że operacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="176a4-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="176a4-108">HOST_E_INTERRUPTED wskazuje, że wywołanie zostało przerwane przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="176a4-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="176a4-109">E_FAIL wskazuje, że wystąpił nieznany, nieodwracalny błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="176a4-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="176a4-110">podczas Liczba bajtów transferowanych podczas przetwarzania żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="176a4-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="176a4-111">podczas Wskaźnik do `OVERLAPPED` struktury, która została przeniesiona do wywołania `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="176a4-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="176a4-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="176a4-112">Return Value</span></span>  
  
|<span data-ttu-id="176a4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="176a4-113">HRESULT</span></span>|<span data-ttu-id="176a4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="176a4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="176a4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="176a4-115">S_OK</span></span>|<span data-ttu-id="176a4-116">`OnComplete`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="176a4-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="176a4-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="176a4-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="176a4-118">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="176a4-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="176a4-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="176a4-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="176a4-120">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="176a4-120">The call timed out.</span></span>|  
|<span data-ttu-id="176a4-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="176a4-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="176a4-122">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="176a4-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="176a4-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="176a4-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="176a4-124">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="176a4-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="176a4-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="176a4-125">E_FAIL</span></span>|<span data-ttu-id="176a4-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="176a4-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="176a4-127">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="176a4-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="176a4-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="176a4-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="176a4-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="176a4-129">Remarks</span></span>  
 <span data-ttu-id="176a4-130">Jeśli Host implementuje abstrakcję ukończenia operacji we/wy, środowisko CLR wykonuje żądania we/wy za pośrednictwem hosta przy użyciu metod [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="176a4-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="176a4-131">Następnie Host wywołuje `OnComplete` metodę w celu powiadomienia środowiska uruchomieniowego o wyniku takich żądań.</span><span class="sxs-lookup"><span data-stu-id="176a4-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="176a4-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="176a4-132">Requirements</span></span>  
 <span data-ttu-id="176a4-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="176a4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="176a4-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="176a4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="176a4-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="176a4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="176a4-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="176a4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176a4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="176a4-137">See also</span></span>

- [<span data-ttu-id="176a4-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="176a4-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="176a4-139">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="176a4-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="176a4-140">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="176a4-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
