---
title: "ICLROnEventManager::UnregisterActionOnEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.UnregisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e8f922207ff347bb6570ede417fdeda71f92d0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="2cc38-102">ICLROnEventManager::UnregisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="2cc38-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="2cc38-103">Wyrejestrowuje wskaźnik wcześniej zarejestrowane wywołanie zwrotne dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2cc38-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cc38-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cc38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cc38-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2cc38-106">[in] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, wskazując zdarzeń, do których chcesz wyrejestrować opisanego przez wskaźnik wywołania zwrotnego `pAction`.</span><span class="sxs-lookup"><span data-stu-id="2cc38-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="2cc38-107">[in] Wskaźnik do [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) obiektu, który został przekazany jako parametr [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2cc38-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cc38-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2cc38-108">Return Value</span></span>  
  
|<span data-ttu-id="2cc38-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cc38-109">HRESULT</span></span>|<span data-ttu-id="2cc38-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2cc38-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cc38-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cc38-111">S_OK</span></span>|<span data-ttu-id="2cc38-112">`UnregisterActionOnEvent`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2cc38-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2cc38-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cc38-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cc38-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="2cc38-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cc38-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cc38-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cc38-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="2cc38-116">The call timed out.</span></span>|  
|<span data-ttu-id="2cc38-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cc38-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cc38-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2cc38-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cc38-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cc38-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cc38-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="2cc38-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cc38-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cc38-121">E_FAIL</span></span>|<span data-ttu-id="2cc38-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2cc38-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cc38-123">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="2cc38-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cc38-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2cc38-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cc38-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cc38-125">Requirements</span></span>  
 <span data-ttu-id="2cc38-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cc38-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc38-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cc38-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cc38-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cc38-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cc38-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc38-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc38-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cc38-130">See Also</span></span>  
 [<span data-ttu-id="2cc38-131">EClrEvent — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2cc38-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="2cc38-132">IActionOnCLREvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="2cc38-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="2cc38-133">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="2cc38-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2cc38-134">ICLROnEventManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="2cc38-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
