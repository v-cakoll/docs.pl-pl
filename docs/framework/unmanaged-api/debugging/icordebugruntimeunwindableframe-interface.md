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
ms.openlocfilehash: f006085aba140264e2a2605adce39924dbe082e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568117"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="67f29-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="67f29-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="67f29-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="67f29-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67f29-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67f29-104">Remarks</span></span>  
 <span data-ttu-id="67f29-105">`ICorDebugRuntimeUnwindableFrame` jest specjalizowanej wersji icordebugframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="67f29-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="67f29-106">Jest on używany przez niezarządzanych metod, które wymagają środowiska uruchomieniowego, aby zwolnić ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="67f29-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="67f29-107">Istniejące konwencje odwijania nie działa, ponieważ nie należy używać kodu kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="67f29-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="67f29-108">Gdy debuger wykryje odwracalnych ramki, należy użyć [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metody na odpoczynek, go, ale należy wykonywać własnej inspekcji.</span><span class="sxs-lookup"><span data-stu-id="67f29-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="67f29-109">Kiedy debuger otrzyma `ICorDebugRuntimeUnwindableFrame`, może wywołać [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metodę, która pobierze kontekście ramki.</span><span class="sxs-lookup"><span data-stu-id="67f29-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67f29-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67f29-110">Requirements</span></span>  
 <span data-ttu-id="67f29-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67f29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67f29-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67f29-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67f29-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67f29-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67f29-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67f29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f29-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67f29-115">See also</span></span>
- [<span data-ttu-id="67f29-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="67f29-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="67f29-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="67f29-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
