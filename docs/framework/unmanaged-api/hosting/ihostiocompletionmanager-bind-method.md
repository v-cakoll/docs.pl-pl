---
title: "IHostIoCompletionManager::Bind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.Bind
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5eba258065c5ddbbf6fad474aed700065b155a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="ae821-102">IHostIoCompletionManager::Bind — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae821-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="ae821-103">Wiąże określone dojście do portu ukończenia operacji We/Wy, która została utworzona przez wywołanie wcześniejszych [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae821-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae821-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae821-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae821-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae821-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="ae821-106">[in] Portu zakończenia We/Wy, do którego należy powiązać `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="ae821-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="ae821-107">Jeśli wartość `hPort` ma wartość null, `hHandle` jest powiązany z domyślnego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="ae821-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="ae821-108">[in] Dojście systemu operacyjnego, aby powiązać `hPort`.</span><span class="sxs-lookup"><span data-stu-id="ae821-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae821-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae821-109">Return Value</span></span>  
  
|<span data-ttu-id="ae821-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae821-110">HRESULT</span></span>|<span data-ttu-id="ae821-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ae821-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae821-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae821-112">S_OK</span></span>|<span data-ttu-id="ae821-113">`Bind`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ae821-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="ae821-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae821-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae821-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ae821-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae821-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae821-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae821-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ae821-117">The call timed out.</span></span>|  
|<span data-ttu-id="ae821-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae821-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae821-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ae821-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae821-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae821-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae821-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ae821-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae821-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae821-122">E_FAIL</span></span>|<span data-ttu-id="ae821-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ae821-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae821-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ae821-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae821-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ae821-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae821-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae821-126">Remarks</span></span>  
 <span data-ttu-id="ae821-127">Portu zakończenia We/Wy jest tworzona przy użyciu wywołania `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="ae821-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="ae821-128">Wywołania CLR `Bind` można powiązać dojścia do tego portu.</span><span class="sxs-lookup"><span data-stu-id="ae821-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae821-129">Po ukończeniu operacji We/Wy żądanie hosta musi wywoływać [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ae821-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae821-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae821-130">Requirements</span></span>  
 <span data-ttu-id="ae821-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae821-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae821-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae821-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae821-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae821-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae821-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae821-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae821-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae821-135">See Also</span></span>  
 [<span data-ttu-id="ae821-136">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ae821-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
