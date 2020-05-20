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
ms.openlocfilehash: 8a9fdcd650e18bb91e2a4e30e5a22fb2a991d25c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703498"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="8eb67-102">ICLROnEventManager::UnregisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="8eb67-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="8eb67-103">Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8eb67-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eb67-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eb67-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="8eb67-106">podczas Jedna z wartości [EClrEvent —](eclrevent-enumeration.md) , wskazująca na zdarzenie, dla którego ma zostać wyrejestrowany wskaźnik wywołania zwrotnego opisany przez `pAction` .</span><span class="sxs-lookup"><span data-stu-id="8eb67-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="8eb67-107">podczas Wskaźnik do obiektu [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , który został przekazano jako parametr do metody [RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8eb67-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8eb67-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8eb67-108">Return Value</span></span>  
  
|<span data-ttu-id="8eb67-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8eb67-109">HRESULT</span></span>|<span data-ttu-id="8eb67-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8eb67-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8eb67-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8eb67-111">S_OK</span></span>|<span data-ttu-id="8eb67-112">`UnregisterActionOnEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="8eb67-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8eb67-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8eb67-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8eb67-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8eb67-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8eb67-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8eb67-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8eb67-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8eb67-116">The call timed out.</span></span>|  
|<span data-ttu-id="8eb67-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8eb67-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8eb67-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8eb67-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8eb67-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8eb67-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8eb67-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8eb67-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8eb67-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8eb67-121">E_FAIL</span></span>|<span data-ttu-id="8eb67-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8eb67-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8eb67-123">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="8eb67-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8eb67-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8eb67-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8eb67-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8eb67-125">Requirements</span></span>  
 <span data-ttu-id="8eb67-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb67-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb67-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8eb67-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8eb67-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8eb67-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8eb67-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb67-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb67-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb67-130">See also</span></span>

- [<span data-ttu-id="8eb67-131">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8eb67-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="8eb67-132">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8eb67-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="8eb67-133">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8eb67-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8eb67-134">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8eb67-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
