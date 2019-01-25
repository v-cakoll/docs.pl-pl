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
ms.openlocfilehash: b969f43e48d7292f695e2355dea0eaa36fd0b73a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593397"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="f67b2-102">IDebuggerThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f67b2-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="f67b2-103">Zawiera metody służące do powiadamiania hosta dotyczące blokowania i odblokowywania wątków przez usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="f67b2-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f67b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f67b2-104">Methods</span></span>  
  
|<span data-ttu-id="f67b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f67b2-105">Method</span></span>|<span data-ttu-id="f67b2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f67b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f67b2-107">ThreadIsBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="f67b2-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="f67b2-108">Powiadamia hosta, którego dotyczy wątku, który wysyła to wywołanie zwrotne do bloku, w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="f67b2-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="f67b2-109">ReleaseAllRuntimeThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="f67b2-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="f67b2-110">Powiadamia hosta, że usług debugowania zamiar Zwolnij wszystkie wątki, które są blokowane.</span><span class="sxs-lookup"><span data-stu-id="f67b2-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="f67b2-111">StartBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="f67b2-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="f67b2-112">Powiadamia hosta, że usług debugowania zamiar start blokuje wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="f67b2-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f67b2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f67b2-113">Requirements</span></span>  
 <span data-ttu-id="f67b2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f67b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f67b2-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f67b2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f67b2-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f67b2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f67b2-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f67b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67b2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f67b2-118">See also</span></span>
- [<span data-ttu-id="f67b2-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f67b2-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
