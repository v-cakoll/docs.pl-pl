---
title: "ICLROnEventManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02a19a3daf72cdfa493b09fa984fe7b50865ed30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="a1327-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1327-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="a1327-103">Udostępnia metody umożliwiające hosta do rejestrowania i wyrejestrowania wywołań zwrotnych dla zdarzenia środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a1327-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1327-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1327-104">Methods</span></span>  
  
|<span data-ttu-id="a1327-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1327-105">Method</span></span>|<span data-ttu-id="a1327-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a1327-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1327-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="a1327-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="a1327-108">Rejestruje wywołanie zwrotne wskaźnik określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1327-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="a1327-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="a1327-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="a1327-110">Wyrejestrowuje wskaźnik wcześniej zarejestrowane wywołanie zwrotne dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1327-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1327-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1327-111">Remarks</span></span>  
 <span data-ttu-id="a1327-112">Umożliwia rejestrowanie i wyrejestrowywanie wywołania zwrotne zdarzeń, host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a1327-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1327-113">Zdarzenia opisanego przez [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) być uruchamiane w więcej niż jeden raz i inne wątki sygnalizują zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a1327-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1327-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1327-114">Requirements</span></span>  
 <span data-ttu-id="a1327-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1327-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1327-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1327-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1327-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1327-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1327-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1327-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1327-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1327-119">See Also</span></span>  
 [<span data-ttu-id="a1327-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a1327-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="a1327-121">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1327-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="a1327-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1327-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a1327-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1327-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
