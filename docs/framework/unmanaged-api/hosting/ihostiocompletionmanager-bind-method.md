---
title: IHostIoCompletionManager::Bind — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fa87026e0d4c93da782be15bef98afa9a0e4dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984363"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="87dc1-102">IHostIoCompletionManager::Bind — Metoda</span><span class="sxs-lookup"><span data-stu-id="87dc1-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="87dc1-103">Wiąże określone dojście do portu ukończenia operacji We/Wy, który został utworzony przez wcześniejsze wywołanie [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="87dc1-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87dc1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87dc1-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87dc1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87dc1-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="87dc1-106">[in] Portu zakończenia We/Wy, dla której chcesz powiązać `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="87dc1-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="87dc1-107">Jeśli wartość `hPort` ma wartość null, `hHandle` jest powiązany z domyślnego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="87dc1-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="87dc1-108">[in] Dojście systemu operacyjnego, aby powiązać `hPort`.</span><span class="sxs-lookup"><span data-stu-id="87dc1-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87dc1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87dc1-109">Return Value</span></span>  
  
|<span data-ttu-id="87dc1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87dc1-110">HRESULT</span></span>|<span data-ttu-id="87dc1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="87dc1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87dc1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="87dc1-112">S_OK</span></span>|<span data-ttu-id="87dc1-113">`Bind` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="87dc1-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="87dc1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87dc1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87dc1-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="87dc1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87dc1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87dc1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87dc1-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="87dc1-117">The call timed out.</span></span>|  
|<span data-ttu-id="87dc1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87dc1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87dc1-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="87dc1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87dc1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87dc1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87dc1-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="87dc1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87dc1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87dc1-122">E_FAIL</span></span>|<span data-ttu-id="87dc1-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="87dc1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87dc1-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="87dc1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87dc1-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="87dc1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87dc1-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87dc1-126">Remarks</span></span>  
 <span data-ttu-id="87dc1-127">Port wykonywania operacji We/Wy jest tworzona przy użyciu wywołania `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="87dc1-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="87dc1-128">CLR wywołuje `Bind` powiązać dojścia do tego portu.</span><span class="sxs-lookup"><span data-stu-id="87dc1-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87dc1-129">Po zakończeniu żądania We/Wy, host musi wywołać [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="87dc1-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87dc1-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87dc1-130">Requirements</span></span>  
 <span data-ttu-id="87dc1-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87dc1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87dc1-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87dc1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87dc1-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87dc1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87dc1-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87dc1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87dc1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87dc1-135">See also</span></span>

- [<span data-ttu-id="87dc1-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87dc1-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
