---
title: ICLRDebugManager::IsDebuggerAttached — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d6c071b3ac68cb38fc85aff65fff49a71ea4275
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970108"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="1f7fc-102">ICLRDebugManager::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f7fc-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="1f7fc-103">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f7fc-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f7fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f7fc-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="1f7fc-106">[out] `true` Jeśli Debuger jest dołączony do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f7fc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f7fc-107">Return Value</span></span>  
  
|<span data-ttu-id="1f7fc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f7fc-108">HRESULT</span></span>|<span data-ttu-id="1f7fc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1f7fc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f7fc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f7fc-110">S_OK</span></span>|<span data-ttu-id="1f7fc-111">`IsDebuggerAttached` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="1f7fc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f7fc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f7fc-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f7fc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f7fc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f7fc-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f7fc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f7fc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f7fc-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f7fc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f7fc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f7fc-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f7fc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f7fc-120">E_FAIL</span></span>|<span data-ttu-id="1f7fc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f7fc-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f7fc-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f7fc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f7fc-124">Remarks</span></span>  
 <span data-ttu-id="1f7fc-125">`IsDebuggerAttached` Zezwalaj hostowi na zapytania CLR w celu ustalenia, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f7fc-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f7fc-126">Requirements</span></span>  
 <span data-ttu-id="1f7fc-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f7fc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f7fc-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f7fc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f7fc-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f7fc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f7fc-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f7fc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7fc-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f7fc-131">See also</span></span>

- [<span data-ttu-id="1f7fc-132">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f7fc-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1f7fc-133">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f7fc-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="1f7fc-134">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f7fc-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
