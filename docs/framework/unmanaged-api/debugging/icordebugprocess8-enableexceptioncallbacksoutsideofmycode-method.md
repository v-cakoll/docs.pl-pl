---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fc7f34059660c273055c3ee24fb6722fda1ef3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466560"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="262a2-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda</span><span class="sxs-lookup"><span data-stu-id="262a2-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="262a2-103">[Obsługiwane w [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="262a2-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="262a2-104">Włącza lub wyłącza niektóre rodzaje [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="262a2-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262a2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="262a2-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="262a2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="262a2-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="262a2-107">[in]</span><span class="sxs-lookup"><span data-stu-id="262a2-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="262a2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="262a2-108">Remarks</span></span>  
 <span data-ttu-id="262a2-109">Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:</span><span class="sxs-lookup"><span data-stu-id="262a2-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="262a2-110">Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie spowoduje wywołanie zwrotne do debugera.</span><span class="sxs-lookup"><span data-stu-id="262a2-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="262a2-111">Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie powoduje wywołanie zwrotne do debugera w przypadku wyjątku, nigdy nie specjalne w kodzie użytkownika (oznacza to ścieżki ze źródła wyjątku do obsługi wyjątków nie zawiera metod oznaczonego jako JustMyCode lub JMC).</span><span class="sxs-lookup"><span data-stu-id="262a2-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="262a2-112">Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="262a2-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262a2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="262a2-113">Requirements</span></span>  
 <span data-ttu-id="262a2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="262a2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="262a2-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="262a2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="262a2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="262a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="262a2-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="262a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262a2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="262a2-118">See also</span></span>
- [<span data-ttu-id="262a2-119">ICorDebugProcess8, interfejs</span><span class="sxs-lookup"><span data-stu-id="262a2-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="262a2-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="262a2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
