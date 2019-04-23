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
ms.openlocfilehash: 7486a094deab16ebbc05f19f1b652126479ce11c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183004"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="8034a-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8034a-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="8034a-103">Udostępnia metody, które umożliwiają hosta rejestrować i wyrejestrowywać wywołania zwrotne dla typowych zdarzeń środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="8034a-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8034a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8034a-104">Methods</span></span>  
  
|<span data-ttu-id="8034a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8034a-105">Method</span></span>|<span data-ttu-id="8034a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8034a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8034a-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="8034a-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="8034a-108">Rejestruje wywołanie zwrotne wskaźnik dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8034a-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="8034a-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="8034a-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="8034a-110">Wyrejestrowuje wskaźnik wcześniej zarejestrowanego wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8034a-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8034a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8034a-111">Remarks</span></span>  
 <span data-ttu-id="8034a-112">Aby rejestrować i wyrejestrowywać wywołania zwrotne zdarzeń, host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8034a-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8034a-113">Zdarzenie opisane przez [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) uruchamiane więcej niż jeden raz i inne wątki w celu sygnalizowania, że zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8034a-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8034a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8034a-114">Requirements</span></span>  
 <span data-ttu-id="8034a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8034a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8034a-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8034a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8034a-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8034a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8034a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8034a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8034a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8034a-119">See also</span></span>

- [<span data-ttu-id="8034a-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8034a-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="8034a-121">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="8034a-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="8034a-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="8034a-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8034a-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8034a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
