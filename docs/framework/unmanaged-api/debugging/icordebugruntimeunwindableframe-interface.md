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
ms.openlocfilehash: 3e2edc64cd9067ed89ae0e309c6a5630319ce835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="70ddf-102">ICorDebugRuntimeUnwindableFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="70ddf-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="70ddf-103">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="70ddf-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70ddf-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70ddf-104">Remarks</span></span>  
 <span data-ttu-id="70ddf-105">`ICorDebugRuntimeUnwindableFrame` to specjalna wersja interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="70ddf-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="70ddf-106">Jest on używany przez niezarządzane metody, które wymagają unwind ramek na stosie bieżącego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70ddf-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="70ddf-107">Istniejące konwencje odwijaniem nie działają, ponieważ nie należy używać JIT skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="70ddf-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="70ddf-108">Gdy debuger widzi unwindable ramki, należy użyć [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metodę unwind go, ale należy wykonać własnej inspekcji.</span><span class="sxs-lookup"><span data-stu-id="70ddf-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="70ddf-109">Gdy debuger odbiera `ICorDebugRuntimeUnwindableFrame`, może wywołać [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda pobierania kontekście ramki.</span><span class="sxs-lookup"><span data-stu-id="70ddf-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ddf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70ddf-110">Requirements</span></span>  
 <span data-ttu-id="70ddf-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70ddf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ddf-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70ddf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70ddf-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70ddf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70ddf-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ddf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ddf-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70ddf-115">See Also</span></span>  
 [<span data-ttu-id="70ddf-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="70ddf-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="70ddf-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="70ddf-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
