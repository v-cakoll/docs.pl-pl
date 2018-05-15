---
title: IDebuggerThreadControl — Interfejs
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619a28d2382aa9cc3130a3130c07fa1e283119e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="2f183-102">IDebuggerThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2f183-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="2f183-103">Udostępnia metody dla powiadamiania hosta o blokowania i odblokowywania wątków przez usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f183-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f183-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f183-104">Methods</span></span>  
  
|<span data-ttu-id="2f183-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f183-105">Method</span></span>|<span data-ttu-id="2f183-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2f183-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f183-107">ThreadIsBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="2f183-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="2f183-108">Powiadamia hosta, którego dotyczy wątku, który wysyła to wywołanie zwrotne do bloku, w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f183-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="2f183-109">ReleaseAllRuntimeThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="2f183-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="2f183-110">Powiadamia host czy usług debugowania zwolniona wszystkie wątki, które są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="2f183-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="2f183-111">StartBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="2f183-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="2f183-112">Powiadamia host czy usług debugowania rozpoczęcia blokuje wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="2f183-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f183-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f183-113">Requirements</span></span>  
 <span data-ttu-id="2f183-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f183-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f183-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f183-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f183-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f183-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f183-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f183-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f183-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f183-118">See Also</span></span>  
 [<span data-ttu-id="2f183-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2f183-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
