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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985533"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="95878-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="95878-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="95878-103">Udostępnia [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody, która wykonuje wywołania zwrotne dla zdarzenia, które zostały zarejestrowane przy użyciu wywołania [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95878-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95878-104">Metody</span><span class="sxs-lookup"><span data-stu-id="95878-104">Methods</span></span>  
  
|<span data-ttu-id="95878-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="95878-105">Method</span></span>|<span data-ttu-id="95878-106">Opis</span><span class="sxs-lookup"><span data-stu-id="95878-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95878-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="95878-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="95878-108">Wykonuje wywołanie zwrotne zarejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="95878-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95878-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95878-109">Requirements</span></span>  
 <span data-ttu-id="95878-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95878-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95878-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95878-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95878-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95878-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95878-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95878-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95878-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95878-114">See also</span></span>

- [<span data-ttu-id="95878-115">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="95878-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="95878-116">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="95878-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="95878-117">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="95878-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="95878-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="95878-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
