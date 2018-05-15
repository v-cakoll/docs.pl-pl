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
ms.openlocfilehash: c22dfa99d8069c060a525a9ae2cbef73d6625898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="df484-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="df484-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="df484-103">Udostępnia metody umożliwiające hosta do rejestrowania i wyrejestrowania wywołań zwrotnych dla zdarzenia środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="df484-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df484-104">Metody</span><span class="sxs-lookup"><span data-stu-id="df484-104">Methods</span></span>  
  
|<span data-ttu-id="df484-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="df484-105">Method</span></span>|<span data-ttu-id="df484-106">Opis</span><span class="sxs-lookup"><span data-stu-id="df484-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df484-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="df484-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="df484-108">Rejestruje wywołanie zwrotne wskaźnik określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="df484-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="df484-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="df484-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="df484-110">Wyrejestrowuje wskaźnik wcześniej zarejestrowane wywołanie zwrotne dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="df484-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df484-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df484-111">Remarks</span></span>  
 <span data-ttu-id="df484-112">Umożliwia rejestrowanie i wyrejestrowywanie wywołania zwrotne zdarzeń, host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="df484-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df484-113">Zdarzenia opisanego przez [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) być uruchamiane w więcej niż jeden raz i inne wątki sygnalizują zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="df484-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df484-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df484-114">Requirements</span></span>  
 <span data-ttu-id="df484-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df484-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df484-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df484-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df484-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df484-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df484-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df484-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df484-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df484-119">See Also</span></span>  
 [<span data-ttu-id="df484-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="df484-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="df484-121">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="df484-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="df484-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="df484-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="df484-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="df484-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
