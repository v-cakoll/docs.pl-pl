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
ms.openlocfilehash: a3018d8477d5abd7d03ad8675503624d2e44e8f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504137"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="81e18-102">ICLROnEventManager::UnregisterActionOnEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="81e18-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="81e18-103">Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="81e18-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81e18-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81e18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81e18-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="81e18-106">podczas Jedna z wartości [EClrEvent —](eclrevent-enumeration.md) , wskazująca na zdarzenie, dla którego ma zostać wyrejestrowany wskaźnik wywołania zwrotnego opisany przez `pAction` .</span><span class="sxs-lookup"><span data-stu-id="81e18-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="81e18-107">podczas Wskaźnik do obiektu [IActionOnCLREvent](iactiononclrevent-interface.md) , który został przekazano jako parametr do metody [RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="81e18-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e18-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81e18-108">Return Value</span></span>  
  
|<span data-ttu-id="81e18-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81e18-109">HRESULT</span></span>|<span data-ttu-id="81e18-110">Opis</span><span class="sxs-lookup"><span data-stu-id="81e18-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81e18-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="81e18-111">S_OK</span></span>|<span data-ttu-id="81e18-112">`UnregisterActionOnEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="81e18-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="81e18-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81e18-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81e18-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="81e18-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81e18-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81e18-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81e18-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="81e18-116">The call timed out.</span></span>|  
|<span data-ttu-id="81e18-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81e18-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81e18-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="81e18-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81e18-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81e18-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81e18-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="81e18-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81e18-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81e18-121">E_FAIL</span></span>|<span data-ttu-id="81e18-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="81e18-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81e18-123">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="81e18-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81e18-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81e18-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81e18-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81e18-125">Requirements</span></span>  
 <span data-ttu-id="81e18-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e18-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e18-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81e18-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81e18-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81e18-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81e18-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e18-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e18-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81e18-130">See also</span></span>

- [<span data-ttu-id="81e18-131">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="81e18-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="81e18-132">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="81e18-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="81e18-133">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="81e18-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="81e18-134">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81e18-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
