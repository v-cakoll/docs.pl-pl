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
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131893"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="53b32-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="53b32-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="53b32-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="53b32-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b32-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53b32-104">Remarks</span></span>  
 <span data-ttu-id="53b32-105">`ICorDebugRuntimeUnwindableFrame` to wyspecjalizowana wersja interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="53b32-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="53b32-106">Jest on używany przez metody niezarządzane, które wymagają wykonania przez środowisko uruchomieniowe ramki na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="53b32-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="53b32-107">Istniejące konwencje odwinięcia nie działają, ponieważ nie używają kodu skompilowanego JIT.</span><span class="sxs-lookup"><span data-stu-id="53b32-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="53b32-108">Gdy debuger widzi niewidocznyą ramkę, powinien użyć metody [ICorDebugStackWalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) , aby ją rozwinięcie, ale powinien wykonać inspekcję.</span><span class="sxs-lookup"><span data-stu-id="53b32-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="53b32-109">Gdy debuger otrzymuje `ICorDebugRuntimeUnwindableFrame`, może wywołać metodę [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) w celu pobrania kontekstu ramki.</span><span class="sxs-lookup"><span data-stu-id="53b32-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b32-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53b32-110">Requirements</span></span>  
 <span data-ttu-id="53b32-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b32-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b32-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="53b32-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53b32-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="53b32-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53b32-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b32-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b32-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53b32-115">See also</span></span>

- [<span data-ttu-id="53b32-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="53b32-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="53b32-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="53b32-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
