---
title: "ICLRDebugManager::IsDebuggerAttached — Metoda"
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
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5abd854e224b19efa72100db0163d61b42b0b63c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="d7ff0-102">ICLRDebugManager::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7ff0-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d7ff0-103">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ff0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7ff0-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7ff0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7ff0-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d7ff0-106">[out] `true` Jeśli Debuger jest dołączony do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7ff0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d7ff0-107">Return Value</span></span>  
  
|<span data-ttu-id="d7ff0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7ff0-108">HRESULT</span></span>|<span data-ttu-id="d7ff0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d7ff0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7ff0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7ff0-110">S_OK</span></span>|<span data-ttu-id="d7ff0-111">`IsDebuggerAttached`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="d7ff0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7ff0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7ff0-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7ff0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7ff0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7ff0-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-115">The call timed out.</span></span>|  
|<span data-ttu-id="d7ff0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7ff0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7ff0-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7ff0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7ff0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7ff0-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7ff0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7ff0-120">E_FAIL</span></span>|<span data-ttu-id="d7ff0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7ff0-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7ff0-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7ff0-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7ff0-124">Remarks</span></span>  
 <span data-ttu-id="d7ff0-125">`IsDebuggerAttached`umożliwia hostowi zapytania CLR w celu ustalenia, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="d7ff0-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ff0-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7ff0-126">Requirements</span></span>  
 <span data-ttu-id="d7ff0-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7ff0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ff0-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7ff0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7ff0-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7ff0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7ff0-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ff0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ff0-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7ff0-131">See Also</span></span>  
 [<span data-ttu-id="d7ff0-132">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7ff0-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d7ff0-133">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7ff0-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="d7ff0-134">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7ff0-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
