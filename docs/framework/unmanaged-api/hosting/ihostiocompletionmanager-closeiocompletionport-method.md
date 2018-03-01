---
title: "IHostIoCompletionManager::CloseIoCompletionPort — Metoda"
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
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e74803cad610d5550ce8b52ce04295247617d907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="d8c53-102">IHostIoCompletionManager::CloseIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="d8c53-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="d8c53-103">Żąda, że host zamknąć portu, która została otwarta za pomocą wcześniejszych wywołania do [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8c53-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8c53-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8c53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8c53-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="d8c53-106">[in] Dojście portu, aby zamknąć.</span><span class="sxs-lookup"><span data-stu-id="d8c53-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8c53-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d8c53-107">Return Value</span></span>  
  
|<span data-ttu-id="d8c53-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8c53-108">HRESULT</span></span>|<span data-ttu-id="d8c53-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d8c53-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8c53-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8c53-110">S_OK</span></span>|<span data-ttu-id="d8c53-111">`CloseIoCompletionPort`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d8c53-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="d8c53-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8c53-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8c53-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d8c53-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8c53-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8c53-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8c53-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d8c53-115">The call timed out.</span></span>|  
|<span data-ttu-id="d8c53-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8c53-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8c53-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d8c53-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8c53-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8c53-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8c53-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d8c53-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8c53-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8c53-120">E_FAIL</span></span>|<span data-ttu-id="d8c53-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d8c53-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8c53-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d8c53-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8c53-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d8c53-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d8c53-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d8c53-124">E_INVALIDARG</span></span>|<span data-ttu-id="d8c53-125">Przekazano nieprawidłowe dojście do portu.</span><span class="sxs-lookup"><span data-stu-id="d8c53-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c53-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8c53-126">Remarks</span></span>  
 <span data-ttu-id="d8c53-127">`hPort`musi być dojściem do portu, która została utworzona przez wywołanie wcześniejszych `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="d8c53-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c53-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8c53-128">Requirements</span></span>  
 <span data-ttu-id="d8c53-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c53-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c53-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8c53-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8c53-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8c53-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8c53-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8c53-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c53-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8c53-133">See Also</span></span>  
 [<span data-ttu-id="d8c53-134">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8c53-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="d8c53-135">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8c53-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
