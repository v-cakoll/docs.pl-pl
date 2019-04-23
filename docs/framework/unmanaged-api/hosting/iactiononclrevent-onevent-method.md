---
title: IActionOnCLREvent::OnEvent — Metoda
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e7045d3b095b6a35be8b55e1066b459e9583c93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147020"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="d5a2a-102">IActionOnCLREvent::OnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5a2a-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="d5a2a-103">Wykonuje wywołania zwrotne dla zdarzenia, które zostały zarejestrowane przy użyciu wywołania [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5a2a-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5a2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5a2a-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="d5a2a-106">[in] Jedną z [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, które wskazuje typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="d5a2a-107">[in] Wskaźnik do obiektu, który zawiera szczegółowe informacje o `event`.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5a2a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5a2a-108">Return Value</span></span>  
  
|<span data-ttu-id="d5a2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5a2a-109">HRESULT</span></span>|<span data-ttu-id="d5a2a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d5a2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5a2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5a2a-111">S_OK</span></span>|<span data-ttu-id="d5a2a-112">`OnEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="d5a2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5a2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5a2a-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5a2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5a2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5a2a-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="d5a2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5a2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5a2a-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5a2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5a2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5a2a-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5a2a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5a2a-121">E_FAIL</span></span>|<span data-ttu-id="d5a2a-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5a2a-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5a2a-124">Kolejne wywołania do dowolnej metody hostowania zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5a2a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5a2a-125">Remarks</span></span>  
 <span data-ttu-id="d5a2a-126">`data` Parametr jest wskaźnikiem do obiektu nieokreślonego typu.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="d5a2a-127">Jeśli `event` parametr jest `Event_DomainUnload`, `data` jest identyfikator liczbowy <xref:System.AppDomain> , został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="d5a2a-128">Hosta można podjąć odpowiednie działania, o których jako klucz przy użyciu tego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="d5a2a-129">Jeśli `event` jest `Event_MDAFired`, `data` jest wskaźnikiem do [mdainfo —](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera dane wyjściowe komunikatu z zarządzanego debugowania Asystenta ustawień (MDA).</span><span class="sxs-lookup"><span data-stu-id="d5a2a-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="d5a2a-130">Mda są funkcją środowiska CLR, które pomogą w debugowaniu, generując XML komunikaty o zdarzeniach, które w przeciwnym razie są trudne do pułapki.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="d5a2a-131">Takie wiadomości może być szczególnie przydatne podczas debugowania przejścia między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d5a2a-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="d5a2a-132">Aby uzyskać więcej informacji, zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="d5a2a-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5a2a-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5a2a-133">Requirements</span></span>  
 <span data-ttu-id="d5a2a-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a2a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a2a-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5a2a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5a2a-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5a2a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5a2a-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a2a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a2a-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5a2a-138">See also</span></span>

- [<span data-ttu-id="d5a2a-139">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d5a2a-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d5a2a-140">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d5a2a-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="d5a2a-141">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5a2a-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="d5a2a-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5a2a-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d5a2a-143">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5a2a-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="d5a2a-144">MDAInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="d5a2a-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
