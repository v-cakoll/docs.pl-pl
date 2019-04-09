---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184837"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="d33f6-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda</span><span class="sxs-lookup"><span data-stu-id="d33f6-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="d33f6-103">[Obsługiwane w [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d33f6-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="d33f6-104">Włącza lub wyłącza niektóre rodzaje [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d33f6-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33f6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d33f6-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d33f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d33f6-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="d33f6-107">[in]</span><span class="sxs-lookup"><span data-stu-id="d33f6-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d33f6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d33f6-108">Remarks</span></span>  
 <span data-ttu-id="d33f6-109">Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:</span><span class="sxs-lookup"><span data-stu-id="d33f6-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="d33f6-110">Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie spowoduje wywołanie zwrotne do debugera.</span><span class="sxs-lookup"><span data-stu-id="d33f6-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="d33f6-111">Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie powoduje wywołanie zwrotne do debugera w przypadku wyjątku, nigdy nie specjalne w kodzie użytkownika (oznacza to ścieżki ze źródła wyjątku do obsługi wyjątków nie zawiera metod oznaczonego jako JustMyCode lub JMC).</span><span class="sxs-lookup"><span data-stu-id="d33f6-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="d33f6-112">Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="d33f6-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d33f6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d33f6-113">Requirements</span></span>  
 <span data-ttu-id="d33f6-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d33f6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d33f6-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d33f6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d33f6-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d33f6-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d33f6-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d33f6-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d33f6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d33f6-118">See also</span></span>

- [<span data-ttu-id="d33f6-119">ICorDebugProcess8 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d33f6-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="d33f6-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d33f6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
