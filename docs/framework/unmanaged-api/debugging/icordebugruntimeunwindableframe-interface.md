---
title: ICorDebugRuntimeUnwindableFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6bc73683a6c37ceaaffc635a58803b71c3b6cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134202"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="2e146-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2e146-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="2e146-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="2e146-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e146-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e146-104">Remarks</span></span>  
 <span data-ttu-id="2e146-105">`ICorDebugRuntimeUnwindableFrame` jest specjalizowanej wersji icordebugframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="2e146-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="2e146-106">Jest on używany przez niezarządzanych metod, które wymagają środowiska uruchomieniowego, aby zwolnić ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="2e146-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="2e146-107">Istniejące konwencje odwijania nie działa, ponieważ nie należy używać kodu kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="2e146-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="2e146-108">Gdy debuger wykryje odwracalnych ramki, należy użyć [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metody na odpoczynek, go, ale należy wykonywać własnej inspekcji.</span><span class="sxs-lookup"><span data-stu-id="2e146-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="2e146-109">Kiedy debuger otrzyma `ICorDebugRuntimeUnwindableFrame`, może wywołać [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metodę, która pobierze kontekście ramki.</span><span class="sxs-lookup"><span data-stu-id="2e146-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e146-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e146-110">Requirements</span></span>  
 <span data-ttu-id="2e146-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e146-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e146-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e146-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e146-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e146-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e146-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e146-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e146-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e146-115">See also</span></span>

- [<span data-ttu-id="2e146-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2e146-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2e146-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2e146-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
