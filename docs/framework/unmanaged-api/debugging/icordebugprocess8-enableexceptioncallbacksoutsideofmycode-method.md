---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f13236c865f9a57d77ebf83ab48e010f06ef08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="83cb1-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda</span><span class="sxs-lookup"><span data-stu-id="83cb1-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="83cb1-103">[Obsługiwane w [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="83cb1-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="83cb1-104">Włącza lub wyłącza niektórych typów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wyjątek wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="83cb1-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83cb1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="83cb1-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83cb1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="83cb1-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="83cb1-107">[in]</span><span class="sxs-lookup"><span data-stu-id="83cb1-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83cb1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83cb1-108">Remarks</span></span>  
 <span data-ttu-id="83cb1-109">Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:</span><span class="sxs-lookup"><span data-stu-id="83cb1-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="83cb1-110">Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie spowoduje wywołanie zwrotne do debugera.</span><span class="sxs-lookup"><span data-stu-id="83cb1-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="83cb1-111">Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie spowoduje wywołanie zwrotne do debugera Jeśli wyjątek nigdy nie specjalne do kodu użytkownika (oznacza to, że ścieżka pochodzenia wyjątek do obsługi wyjątków ma żadna metoda oznaczona jako JustMyCode lub JMC).</span><span class="sxs-lookup"><span data-stu-id="83cb1-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="83cb1-112">Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="83cb1-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83cb1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83cb1-113">Requirements</span></span>  
 <span data-ttu-id="83cb1-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83cb1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83cb1-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83cb1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83cb1-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83cb1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83cb1-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83cb1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cb1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83cb1-118">See Also</span></span>  
 [<span data-ttu-id="83cb1-119">ICorDebugProcess8, interfejs</span><span class="sxs-lookup"><span data-stu-id="83cb1-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="83cb1-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="83cb1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
