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
ms.openlocfilehash: a216a2925382016adeb100554bdceefdf3ee902b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616063"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="56fc5-102">IActionOnCLREvent::OnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="56fc5-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="56fc5-103">Wykonuje wywołania zwrotne dla zdarzeń, które zostały zarejestrowane za pomocą wywołania metody [ICLROnEventManager:: RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="56fc5-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56fc5-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56fc5-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="56fc5-106">podczas Jedna z wartości [EClrEvent —](eclrevent-enumeration.md) , która wskazuje typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="56fc5-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="56fc5-107">podczas Wskaźnik do obiektu, który zawiera szczegółowe informacje o `event` .</span><span class="sxs-lookup"><span data-stu-id="56fc5-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56fc5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56fc5-108">Return Value</span></span>  
  
|<span data-ttu-id="56fc5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56fc5-109">HRESULT</span></span>|<span data-ttu-id="56fc5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="56fc5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56fc5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="56fc5-111">S_OK</span></span>|<span data-ttu-id="56fc5-112">`OnEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="56fc5-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="56fc5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56fc5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56fc5-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="56fc5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56fc5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56fc5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56fc5-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="56fc5-116">The call timed out.</span></span>|  
|<span data-ttu-id="56fc5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56fc5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56fc5-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="56fc5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56fc5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56fc5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56fc5-120">Zdarzenie zostało anulowane podczas oczekiwania zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="56fc5-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56fc5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56fc5-121">E_FAIL</span></span>|<span data-ttu-id="56fc5-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="56fc5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56fc5-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="56fc5-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56fc5-124">Kolejne wywołania metody hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="56fc5-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56fc5-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56fc5-125">Remarks</span></span>  
 <span data-ttu-id="56fc5-126">`data`Parametr jest wskaźnikiem do obiektu nieokreślonego typu.</span><span class="sxs-lookup"><span data-stu-id="56fc5-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="56fc5-127">Jeśli `event` parametr jest `Event_DomainUnload` , `data` jest identyfikatorem liczbowym <xref:System.AppDomain> , który został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="56fc5-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="56fc5-128">Host może wykonać odpowiednią akcję przy użyciu tego identyfikatora jako klucza.</span><span class="sxs-lookup"><span data-stu-id="56fc5-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="56fc5-129">Jeśli `event` jest `Event_MDAFired` , `data` jest wskaźnikiem do wystąpienia [MDAInfo —](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , które zawiera komunikat wyjściowy z zarządzanego asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="56fc5-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="56fc5-130">MDA to funkcja środowiska CLR, która pomaga deweloperom w debugowaniu, generując komunikaty XML o zdarzeniach, które w przeciwnym razie są trudne do pułapki.</span><span class="sxs-lookup"><span data-stu-id="56fc5-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="56fc5-131">Takie komunikaty mogą być szczególnie przydatne w przypadku przejść debugowania między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="56fc5-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="56fc5-132">Aby uzyskać więcej informacji, zobacz [Diagnozowanie błędów przy użyciu asystentów debugowania zarządzanego](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="56fc5-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fc5-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56fc5-133">Requirements</span></span>  
 <span data-ttu-id="56fc5-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fc5-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fc5-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="56fc5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56fc5-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56fc5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56fc5-137">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fc5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fc5-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56fc5-138">See also</span></span>

- [<span data-ttu-id="56fc5-139">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="56fc5-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="56fc5-140">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="56fc5-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="56fc5-141">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56fc5-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="56fc5-142">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56fc5-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="56fc5-143">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="56fc5-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="56fc5-144">MDAInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="56fc5-144">MDAInfo Structure</span></span>](mdainfo-structure.md)
