---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 136dab5c05c310d85a5e18bcdc6da0de901d3ace
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227473"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="1342a-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="1342a-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="1342a-103">Powiadamia hosta, że usług debugowania zamiar Zwolnij wszystkie wątki, które są blokowane.</span><span class="sxs-lookup"><span data-stu-id="1342a-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1342a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1342a-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="1342a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1342a-105">Remarks</span></span>  
 <span data-ttu-id="1342a-106">`ReleaseAllRuntimeThreads` Metoda nigdy nie zostanie wywołana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1342a-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="1342a-107">Jeśli host ma zablokowany wątek środowiska uruchomieniowego, jego powinien zwolnij go teraz.</span><span class="sxs-lookup"><span data-stu-id="1342a-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1342a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1342a-108">Requirements</span></span>  
 <span data-ttu-id="1342a-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1342a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1342a-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1342a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1342a-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1342a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1342a-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1342a-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1342a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1342a-113">See also</span></span>

- [<span data-ttu-id="1342a-114">IDebuggerThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1342a-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
