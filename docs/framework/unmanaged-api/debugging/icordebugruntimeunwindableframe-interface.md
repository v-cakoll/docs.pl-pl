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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791920"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="c0563-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0563-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="c0563-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="c0563-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0563-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0563-104">Remarks</span></span>  
 <span data-ttu-id="c0563-105">`ICorDebugRuntimeUnwindableFrame` to wyspecjalizowana wersja interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="c0563-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="c0563-106">Jest on używany przez metody niezarządzane, które wymagają wykonania przez środowisko uruchomieniowe ramki na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="c0563-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="c0563-107">Istniejące konwencje odwinięcia nie działają, ponieważ nie używają kodu skompilowanego JIT.</span><span class="sxs-lookup"><span data-stu-id="c0563-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="c0563-108">Gdy debuger widzi niewidocznyą ramkę, powinien użyć metody [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) , aby ją rozwinięcie, ale powinien wykonać inspekcję.</span><span class="sxs-lookup"><span data-stu-id="c0563-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="c0563-109">Gdy debuger otrzymuje `ICorDebugRuntimeUnwindableFrame`, może wywołać metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) w celu pobrania kontekstu ramki.</span><span class="sxs-lookup"><span data-stu-id="c0563-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0563-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0563-110">Requirements</span></span>  
 <span data-ttu-id="c0563-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0563-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0563-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0563-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0563-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c0563-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0563-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0563-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0563-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0563-115">See also</span></span>

- [<span data-ttu-id="c0563-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c0563-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c0563-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c0563-117">Debugging</span></span>](index.md)
