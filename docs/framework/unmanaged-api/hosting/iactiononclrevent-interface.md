---
title: IActionOnCLREvent — Interfejs
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9277fe2c241ce4f502339de826dccd08a2ce8055
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126959"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="efb85-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="efb85-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="efb85-103">Udostępnia metodę [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , która wykonuje wywołania zwrotne dla zdarzeń, które zostały zarejestrowane przy użyciu wywołania metody [ICLROnEventManager:: RegisterActionOnEvent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="efb85-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efb85-104">Metody</span><span class="sxs-lookup"><span data-stu-id="efb85-104">Methods</span></span>  
  
|<span data-ttu-id="efb85-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="efb85-105">Method</span></span>|<span data-ttu-id="efb85-106">Opis</span><span class="sxs-lookup"><span data-stu-id="efb85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efb85-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="efb85-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="efb85-108">Wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="efb85-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="efb85-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efb85-109">Requirements</span></span>  
 <span data-ttu-id="efb85-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efb85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efb85-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efb85-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efb85-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efb85-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efb85-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efb85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb85-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efb85-114">See also</span></span>

- [<span data-ttu-id="efb85-115">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="efb85-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="efb85-116">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="efb85-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="efb85-117">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="efb85-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="efb85-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="efb85-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
