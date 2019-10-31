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
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133156"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="e8dc4-102">IDebuggerThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e8dc4-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="e8dc4-103">Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8dc4-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8dc4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e8dc4-104">Methods</span></span>  
  
|<span data-ttu-id="e8dc4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8dc4-105">Method</span></span>|<span data-ttu-id="e8dc4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e8dc4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8dc4-107">ThreadIsBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="e8dc4-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="e8dc4-108">Powiadamia hosta, że wątek wysyłający to wywołanie zwrotne ma zostać zablokowany w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8dc4-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="e8dc4-109">ReleaseAllRuntimeThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="e8dc4-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="e8dc4-110">Powiadamia hosta o wydaniu wszystkich zablokowanych wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8dc4-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="e8dc4-111">StartBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="e8dc4-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="e8dc4-112">Powiadamia hosta o konieczności rozpoczęcia blokowania wszystkich wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8dc4-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8dc4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8dc4-113">Requirements</span></span>  
 <span data-ttu-id="e8dc4-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8dc4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8dc4-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8dc4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8dc4-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8dc4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8dc4-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8dc4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8dc4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8dc4-118">See also</span></span>

- [<span data-ttu-id="e8dc4-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e8dc4-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
