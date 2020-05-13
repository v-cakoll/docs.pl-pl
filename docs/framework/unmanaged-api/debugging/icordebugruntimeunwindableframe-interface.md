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
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379385"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="cfca3-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cfca3-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="cfca3-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="cfca3-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfca3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfca3-104">Remarks</span></span>  
 <span data-ttu-id="cfca3-105">`ICorDebugRuntimeUnwindableFrame`to wyspecjalizowana wersja interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="cfca3-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="cfca3-106">Jest on używany przez metody niezarządzane, które wymagają wykonania przez środowisko uruchomieniowe ramki na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="cfca3-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="cfca3-107">Istniejące konwencje odwinięcia nie działają, ponieważ nie używają kodu skompilowanego JIT.</span><span class="sxs-lookup"><span data-stu-id="cfca3-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="cfca3-108">Gdy debuger widzi niewidocznyą ramkę, powinien użyć metody [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) , aby ją rozwinięcie, ale powinien wykonać inspekcję.</span><span class="sxs-lookup"><span data-stu-id="cfca3-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="cfca3-109">Gdy debuger odbiera `ICorDebugRuntimeUnwindableFrame` , może wywołać metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) w celu pobrania kontekstu ramki.</span><span class="sxs-lookup"><span data-stu-id="cfca3-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfca3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfca3-110">Requirements</span></span>  
 <span data-ttu-id="cfca3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfca3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfca3-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfca3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfca3-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cfca3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfca3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfca3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfca3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfca3-115">See also</span></span>

- [<span data-ttu-id="cfca3-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cfca3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfca3-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cfca3-117">Debugging</span></span>](index.md)
