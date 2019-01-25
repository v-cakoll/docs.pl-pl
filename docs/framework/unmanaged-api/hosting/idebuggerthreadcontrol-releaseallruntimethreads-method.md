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
ms.openlocfilehash: a5e2501a5ab62c6aaef2b3f754f9eed10e4e4b97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505028"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="744c8-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="744c8-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="744c8-103">Powiadamia hosta, że usług debugowania zamiar Zwolnij wszystkie wątki, które są blokowane.</span><span class="sxs-lookup"><span data-stu-id="744c8-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="744c8-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="744c8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="744c8-105">Remarks</span></span>  
 <span data-ttu-id="744c8-106">`ReleaseAllRuntimeThreads` Metoda nigdy nie zostanie wywołana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="744c8-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="744c8-107">Jeśli host ma zablokowany wątek środowiska uruchomieniowego, jego powinien zwolnij go teraz.</span><span class="sxs-lookup"><span data-stu-id="744c8-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="744c8-108">Requirements</span></span>  
 <span data-ttu-id="744c8-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744c8-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="744c8-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="744c8-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="744c8-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="744c8-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744c8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="744c8-113">See also</span></span>
- [<span data-ttu-id="744c8-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="744c8-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
