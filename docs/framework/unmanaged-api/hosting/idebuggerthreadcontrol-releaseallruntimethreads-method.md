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
ms.openlocfilehash: 09895294c4678cdb1dd033076cfb42853aa06b2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780504"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="a1fea-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1fea-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="a1fea-103">Powiadamia hosta, że usług debugowania zamiar Zwolnij wszystkie wątki, które są blokowane.</span><span class="sxs-lookup"><span data-stu-id="a1fea-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1fea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1fea-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1fea-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1fea-105">Remarks</span></span>  
 <span data-ttu-id="a1fea-106">`ReleaseAllRuntimeThreads` Metoda nigdy nie zostanie wywołana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a1fea-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="a1fea-107">Jeśli host ma zablokowany wątek środowiska uruchomieniowego, jego powinien zwolnij go teraz.</span><span class="sxs-lookup"><span data-stu-id="a1fea-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1fea-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1fea-108">Requirements</span></span>  
 <span data-ttu-id="a1fea-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1fea-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1fea-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1fea-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1fea-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1fea-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1fea-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1fea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fea-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1fea-113">See also</span></span>

- [<span data-ttu-id="a1fea-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1fea-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
