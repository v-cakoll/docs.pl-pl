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
ms.openlocfilehash: 4068166438c524ad1c0ed4efe455b1f66b6641d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140831"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="ea702-102">ICLROnEventManager::RegisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea702-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="ea702-103">Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea702-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea702-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea702-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea702-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea702-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="ea702-106">podczas Jedna z wartości [EClrEvent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , wskazująca na zdarzenie, dla którego ma zostać zarejestrowany wskaźnik wywołania zwrotnego opisany przez `pAction`.</span><span class="sxs-lookup"><span data-stu-id="ea702-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="ea702-107">podczas Wskaźnik do obiektu [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , który jest wywoływany po uruchomieniu zarejestrowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea702-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea702-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ea702-108">Return Value</span></span>  
  
|<span data-ttu-id="ea702-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea702-109">HRESULT</span></span>|<span data-ttu-id="ea702-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ea702-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea702-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea702-111">S_OK</span></span>|<span data-ttu-id="ea702-112">`RegisterActionOnEvent` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="ea702-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="ea702-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea702-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea702-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ea702-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea702-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea702-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea702-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ea702-116">The call timed out.</span></span>|  
|<span data-ttu-id="ea702-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea702-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea702-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ea702-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea702-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea702-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea702-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ea702-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea702-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea702-121">E_FAIL</span></span>|<span data-ttu-id="ea702-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ea702-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea702-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ea702-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea702-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea702-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea702-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea702-125">Remarks</span></span>  
 <span data-ttu-id="ea702-126">Host może rejestrować wywołania zwrotne dla jednego lub obu typów zdarzeń opisanych przez `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="ea702-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="ea702-127">Host pobiera interfejs `ICLROnEventManager`, wywołując metodę [ICLRControl:: GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ea702-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea702-128">Zdarzenia, które `RegisterActionOnEvent` rejestry mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ea702-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea702-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea702-129">Requirements</span></span>  
 <span data-ttu-id="ea702-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea702-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea702-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea702-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea702-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea702-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea702-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea702-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea702-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea702-134">See also</span></span>

- [<span data-ttu-id="ea702-135">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea702-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="ea702-136">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea702-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="ea702-137">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea702-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ea702-138">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea702-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
