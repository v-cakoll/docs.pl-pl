---
title: ICLROnEventManager::RegisterActionOnEvent — Metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68a8493a9eb5177844e81ef7a9612f979ffe89c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216499"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="9d8e9-102">ICLROnEventManager::RegisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d8e9-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="9d8e9-103">Rejestruje wywołanie zwrotne wskaźnik dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d8e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d8e9-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d8e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d8e9-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="9d8e9-106">[in] Jedną z [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, wskazujący zdarzenia, dla którego ma zostać zarejestrowany opisanego przez wskaźnik wywołania zwrotnego `pAction`.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="9d8e9-107">[in] Wskaźnik do [iactiononclrevent —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) obiektu, która jest wywoływana, gdy zostanie wyzwolony zarejestrowanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d8e9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d8e9-108">Return Value</span></span>  
  
|<span data-ttu-id="9d8e9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d8e9-109">HRESULT</span></span>|<span data-ttu-id="9d8e9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9d8e9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d8e9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d8e9-111">S_OK</span></span>|`RegisterActionOnEvent` <span data-ttu-id="9d8e9-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-112">returned successfully.</span></span>|  
|<span data-ttu-id="9d8e9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d8e9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d8e9-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d8e9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d8e9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d8e9-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-116">The call timed out.</span></span>|  
|<span data-ttu-id="9d8e9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d8e9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d8e9-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d8e9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d8e9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d8e9-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d8e9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d8e9-121">E_FAIL</span></span>|<span data-ttu-id="9d8e9-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d8e9-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d8e9-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d8e9-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d8e9-125">Remarks</span></span>  
 <span data-ttu-id="9d8e9-126">Host może rejestrowanie wywołań zwrotnych przynajmniej jedna z dwóch typach zdarzeń opisanego przez `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="9d8e9-127">Pobiera hosta `ICLROnEventManager` interfejsu, wywołując [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d8e9-128">Zdarzenia, `RegisterActionOnEvent` rejestrów może uruchamiane więcej niż jeden raz i inne wątki w celu sygnalizowania, że zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9d8e9-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d8e9-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d8e9-129">Requirements</span></span>  
 <span data-ttu-id="9d8e9-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d8e9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d8e9-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d8e9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d8e9-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d8e9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9d8e9-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9d8e9-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d8e9-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d8e9-134">See also</span></span>

- [<span data-ttu-id="9d8e9-135">EClrEvent — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9d8e9-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="9d8e9-136">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d8e9-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="9d8e9-137">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d8e9-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9d8e9-138">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d8e9-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
