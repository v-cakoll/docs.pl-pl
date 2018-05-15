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
ms.openlocfilehash: 5b3623c886a48cc938be017f955fbdac1df3f10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="caec3-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="caec3-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="caec3-103">Powiadamia host czy usług debugowania zwolniona wszystkie wątki, które są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="caec3-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caec3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="caec3-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="caec3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caec3-105">Remarks</span></span>  
 <span data-ttu-id="caec3-106">`ReleaseAllRuntimeThreads` Metoda nigdy nie zostanie wywołana w wątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="caec3-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="caec3-107">Jeśli host ma zablokowane wątku czasu wykonywania, go należy zwolnić go teraz.</span><span class="sxs-lookup"><span data-stu-id="caec3-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caec3-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caec3-108">Requirements</span></span>  
 <span data-ttu-id="caec3-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caec3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caec3-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="caec3-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="caec3-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="caec3-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caec3-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caec3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caec3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caec3-113">See Also</span></span>  
 [<span data-ttu-id="caec3-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="caec3-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
