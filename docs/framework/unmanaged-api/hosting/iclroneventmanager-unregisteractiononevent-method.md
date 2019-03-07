---
title: ICLROnEventManager::UnregisterActionOnEvent — Metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fcc5a6c2f2aa6f22a243c53898cdeda807b6774
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471824"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="0f433-102">ICLROnEventManager::UnregisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f433-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="0f433-103">Wyrejestrowuje wskaźnik wcześniej zarejestrowanego wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f433-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f433-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f433-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f433-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="0f433-106">[in] Jedną z [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, wskazujący zdarzeń, do których chcesz wyrejestrować opisanego przez wskaźnik wywołania zwrotnego `pAction`.</span><span class="sxs-lookup"><span data-stu-id="0f433-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="0f433-107">[in] Wskaźnik do [iactiononclrevent —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) obiektu, który został przekazany jako parametr do [registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0f433-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f433-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f433-108">Return Value</span></span>  
  
|<span data-ttu-id="0f433-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f433-109">HRESULT</span></span>|<span data-ttu-id="0f433-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0f433-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f433-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f433-111">S_OK</span></span>|<span data-ttu-id="0f433-112">`UnregisterActionOnEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0f433-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0f433-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f433-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f433-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0f433-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f433-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f433-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f433-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0f433-116">The call timed out.</span></span>|  
|<span data-ttu-id="0f433-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f433-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f433-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="0f433-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f433-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f433-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f433-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0f433-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f433-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f433-121">E_FAIL</span></span>|<span data-ttu-id="0f433-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0f433-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f433-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0f433-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f433-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f433-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f433-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f433-125">Requirements</span></span>  
 <span data-ttu-id="0f433-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f433-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f433-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f433-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f433-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f433-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f433-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f433-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f433-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f433-130">See also</span></span>
- [<span data-ttu-id="0f433-131">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0f433-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="0f433-132">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f433-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="0f433-133">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f433-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="0f433-134">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f433-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
