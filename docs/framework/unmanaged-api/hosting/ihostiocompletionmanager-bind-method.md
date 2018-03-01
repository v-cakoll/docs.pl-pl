---
title: "IHostIoCompletionManager::Bind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34de8c04e248d2973e9b27c10da9313db5077ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="04094-102">IHostIoCompletionManager::Bind — Metoda</span><span class="sxs-lookup"><span data-stu-id="04094-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="04094-103">Wiąże określone dojście do portu ukończenia operacji We/Wy, która została utworzona przez wywołanie wcześniejszych [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="04094-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04094-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04094-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04094-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04094-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="04094-106">[in] Portu zakończenia We/Wy, do którego należy powiązać `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="04094-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="04094-107">Jeśli wartość `hPort` ma wartość null, `hHandle` jest powiązany z domyślnego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="04094-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="04094-108">[in] Dojście systemu operacyjnego, aby powiązać `hPort`.</span><span class="sxs-lookup"><span data-stu-id="04094-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04094-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04094-109">Return Value</span></span>  
  
|<span data-ttu-id="04094-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04094-110">HRESULT</span></span>|<span data-ttu-id="04094-111">Opis</span><span class="sxs-lookup"><span data-stu-id="04094-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04094-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="04094-112">S_OK</span></span>|<span data-ttu-id="04094-113">`Bind`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="04094-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="04094-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04094-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04094-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="04094-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04094-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04094-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04094-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="04094-117">The call timed out.</span></span>|  
|<span data-ttu-id="04094-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04094-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04094-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="04094-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04094-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04094-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04094-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="04094-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04094-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04094-122">E_FAIL</span></span>|<span data-ttu-id="04094-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="04094-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04094-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="04094-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04094-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04094-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04094-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04094-126">Remarks</span></span>  
 <span data-ttu-id="04094-127">Portu zakończenia We/Wy jest tworzona przy użyciu wywołania `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="04094-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="04094-128">Wywołania CLR `Bind` można powiązać dojścia do tego portu.</span><span class="sxs-lookup"><span data-stu-id="04094-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04094-129">Po ukończeniu operacji We/Wy żądanie hosta musi wywoływać [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="04094-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04094-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04094-130">Requirements</span></span>  
 <span data-ttu-id="04094-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04094-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04094-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04094-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04094-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04094-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04094-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04094-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04094-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04094-135">See Also</span></span>  
 [<span data-ttu-id="04094-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="04094-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
