---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9324e1596913fdafb13239dbefd631cbe3c6ffe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780488"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="3521c-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="3521c-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="3521c-103">Powiadamia hosta, którego dotyczy wątku, który wysyła to wywołanie zwrotne do bloku, w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="3521c-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3521c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3521c-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="3521c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3521c-105">Remarks</span></span>  
 <span data-ttu-id="3521c-106">`ThreadIsBlockingForDebugger` Zawsze metoda zostanie wywołana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3521c-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="3521c-107">`ThreadIsBlockingForDebugger` Metoda daje hosta możliwość wykonania kolejnej akcji podczas blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="3521c-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3521c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3521c-108">Requirements</span></span>  
 <span data-ttu-id="3521c-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3521c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3521c-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3521c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3521c-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3521c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3521c-112">**NET Framework w wersji:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3521c-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3521c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3521c-113">See also</span></span>

- [<span data-ttu-id="3521c-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="3521c-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
