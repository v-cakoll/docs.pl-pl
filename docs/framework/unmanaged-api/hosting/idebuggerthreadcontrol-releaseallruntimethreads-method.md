---
title: "IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6e2c4032a0765083177df9a6d7d5206448f566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="59f76-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="59f76-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="59f76-103">Powiadamia host czy usług debugowania zwolniona wszystkie wątki, które są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="59f76-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f76-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59f76-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="59f76-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59f76-105">Remarks</span></span>  
 <span data-ttu-id="59f76-106">`ReleaseAllRuntimeThreads` Metoda nigdy nie zostanie wywołana w wątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59f76-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="59f76-107">Jeśli host ma zablokowane wątku czasu wykonywania, go należy zwolnić go teraz.</span><span class="sxs-lookup"><span data-stu-id="59f76-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f76-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59f76-108">Requirements</span></span>  
 <span data-ttu-id="59f76-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f76-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f76-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59f76-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59f76-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59f76-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59f76-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f76-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f76-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59f76-113">See Also</span></span>  
 [<span data-ttu-id="59f76-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="59f76-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
