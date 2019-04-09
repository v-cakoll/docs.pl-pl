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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180523"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="0120c-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0120c-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="0120c-103">Udostępnia [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody, która wykonuje wywołania zwrotne dla zdarzenia, które zostały zarejestrowane przy użyciu wywołania [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0120c-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0120c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0120c-104">Methods</span></span>  
  
|<span data-ttu-id="0120c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0120c-105">Method</span></span>|<span data-ttu-id="0120c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0120c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0120c-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="0120c-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="0120c-108">Wykonuje wywołanie zwrotne zarejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0120c-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0120c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0120c-109">Requirements</span></span>  
 <span data-ttu-id="0120c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0120c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0120c-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0120c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0120c-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0120c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0120c-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0120c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0120c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0120c-114">See also</span></span>

- [<span data-ttu-id="0120c-115">EClrEvent — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0120c-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="0120c-116">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0120c-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="0120c-117">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0120c-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="0120c-118">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0120c-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
