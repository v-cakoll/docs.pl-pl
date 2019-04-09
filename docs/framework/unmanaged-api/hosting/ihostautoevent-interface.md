---
title: IHostAutoEvent — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb5fea403f8210ea93d240aa3aabd4325524b987
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080946"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="7427a-102">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7427a-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="7427a-103">Udostępnia reprezentację wdrożenia hosta zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="7427a-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7427a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7427a-104">Methods</span></span>  
  
|<span data-ttu-id="7427a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7427a-105">Method</span></span>|<span data-ttu-id="7427a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7427a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7427a-107">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="7427a-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="7427a-108">Ustawia bieżący `IHostAutoEvent` wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="7427a-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="7427a-109">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="7427a-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="7427a-110">Powoduje, że bieżący `IHostAutoEvent` wystąpienie poczekać, aż zdarzenia jest właścicielem lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="7427a-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7427a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7427a-111">Requirements</span></span>  
 <span data-ttu-id="7427a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7427a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7427a-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7427a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7427a-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7427a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7427a-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7427a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7427a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7427a-116">See also</span></span>

- [<span data-ttu-id="7427a-117">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7427a-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7427a-118">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7427a-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="7427a-119">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7427a-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="7427a-120">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7427a-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
