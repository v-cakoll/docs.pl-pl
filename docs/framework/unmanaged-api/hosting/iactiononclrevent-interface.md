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
ms.openlocfilehash: 24191e93d0d8b27d01a914cae76c9ff4e0a7182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="ca1a4-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ca1a4-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="ca1a4-103">Udostępnia [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę, która wykonuje wywołania zwrotne na zdarzenia, które zostały zarejestrowane przy użyciu wywołania [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ca1a4-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca1a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca1a4-104">Methods</span></span>  
  
|<span data-ttu-id="ca1a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca1a4-105">Method</span></span>|<span data-ttu-id="ca1a4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ca1a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca1a4-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="ca1a4-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="ca1a4-108">Wykonuje wywołanie zwrotne zarejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca1a4-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca1a4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca1a4-109">Requirements</span></span>  
 <span data-ttu-id="ca1a4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca1a4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca1a4-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca1a4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca1a4-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca1a4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca1a4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca1a4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1a4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca1a4-114">See Also</span></span>  
 [<span data-ttu-id="ca1a4-115">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ca1a4-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="ca1a4-116">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca1a4-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="ca1a4-117">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca1a4-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="ca1a4-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca1a4-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
