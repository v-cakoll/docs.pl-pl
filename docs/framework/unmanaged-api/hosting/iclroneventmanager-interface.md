---
title: ICLROnEventManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3633db69877db771d919c9f43da4809f8321f77c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951198"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="c3414-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c3414-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="c3414-103">Zapewnia metody, które pozwalają hostowi rejestrować i wyrejestrować wywołania zwrotne dla zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c3414-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3414-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c3414-104">Methods</span></span>  
  
|<span data-ttu-id="c3414-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c3414-105">Method</span></span>|<span data-ttu-id="c3414-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c3414-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3414-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="c3414-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="c3414-108">Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3414-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="c3414-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="c3414-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="c3414-110">Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3414-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3414-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3414-111">Remarks</span></span>  
 <span data-ttu-id="c3414-112">Aby zarejestrować i wyrejestrować wywołania zwrotne zdarzeń, Host pobiera odwołanie do `ICLROnEventManager` , wywołując metodę [ICLRControl:: GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3414-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3414-113">Zdarzenia opisane przez [EClrEvent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c3414-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3414-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3414-114">Requirements</span></span>  
 <span data-ttu-id="c3414-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3414-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3414-116">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3414-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3414-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3414-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3414-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3414-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3414-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3414-119">See also</span></span>

- [<span data-ttu-id="c3414-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c3414-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="c3414-121">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3414-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="c3414-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3414-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c3414-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3414-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
