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
ms.openlocfilehash: 9ae1aa6590366468166916e6a92d0b356eb37c27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133152"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="ad04c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad04c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="ad04c-103">Powiadamia hosta o wydaniu wszystkich zablokowanych wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="ad04c-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad04c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad04c-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad04c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad04c-105">Remarks</span></span>  
 <span data-ttu-id="ad04c-106">Metoda `ReleaseAllRuntimeThreads` nigdy nie będzie wywoływana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad04c-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="ad04c-107">Jeśli host ma zablokowany wątek uruchomieniowy, powinien go teraz wydać.</span><span class="sxs-lookup"><span data-stu-id="ad04c-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad04c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad04c-108">Requirements</span></span>  
 <span data-ttu-id="ad04c-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad04c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad04c-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad04c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad04c-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad04c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad04c-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad04c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad04c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad04c-113">See also</span></span>

- [<span data-ttu-id="ad04c-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad04c-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
