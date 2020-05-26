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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805280"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="63c30-102">IDebuggerThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63c30-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="63c30-103">Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="63c30-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63c30-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63c30-104">Methods</span></span>  
  
|<span data-ttu-id="63c30-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63c30-105">Method</span></span>|<span data-ttu-id="63c30-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63c30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63c30-107">ThreadIsBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="63c30-107">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="63c30-108">Powiadamia hosta, że wątek wysyłający to wywołanie zwrotne ma zostać zablokowany w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="63c30-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="63c30-109">ReleaseAllRuntimeThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="63c30-109">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="63c30-110">Powiadamia hosta o wydaniu wszystkich zablokowanych wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="63c30-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="63c30-111">StartBlockingForDebugger, metoda</span><span class="sxs-lookup"><span data-stu-id="63c30-111">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="63c30-112">Powiadamia hosta o konieczności rozpoczęcia blokowania wszystkich wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="63c30-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63c30-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63c30-113">Requirements</span></span>  
 <span data-ttu-id="63c30-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c30-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c30-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63c30-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63c30-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63c30-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63c30-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c30-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63c30-118">See also</span></span>

- [<span data-ttu-id="63c30-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63c30-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
