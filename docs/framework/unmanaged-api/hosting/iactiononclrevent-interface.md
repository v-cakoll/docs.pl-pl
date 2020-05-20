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
ms.openlocfilehash: 4e72cd8bee2cb4f35155d7b99cfe8d9cf63f463a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616076"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="49d79-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="49d79-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="49d79-103">Udostępnia metodę [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , która wykonuje wywołania zwrotne dla zdarzeń, które zostały zarejestrowane przy użyciu wywołania metody [ICLROnEventManager:: RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="49d79-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49d79-104">Metody</span><span class="sxs-lookup"><span data-stu-id="49d79-104">Methods</span></span>  
  
|<span data-ttu-id="49d79-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="49d79-105">Method</span></span>|<span data-ttu-id="49d79-106">Opis</span><span class="sxs-lookup"><span data-stu-id="49d79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49d79-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="49d79-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="49d79-108">Wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="49d79-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49d79-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49d79-109">Requirements</span></span>  
 <span data-ttu-id="49d79-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d79-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d79-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49d79-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49d79-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49d79-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49d79-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d79-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49d79-114">See also</span></span>

- [<span data-ttu-id="49d79-115">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="49d79-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="49d79-116">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="49d79-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="49d79-117">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="49d79-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="49d79-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="49d79-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
