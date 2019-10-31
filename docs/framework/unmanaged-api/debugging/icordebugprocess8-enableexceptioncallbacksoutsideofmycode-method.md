---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123376"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="b6762-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda</span><span class="sxs-lookup"><span data-stu-id="b6762-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="b6762-103">[Obsługiwane w .NET Framework 4,6 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b6762-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="b6762-104">Włącza lub wyłącza określone typy wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b6762-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6762-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6762-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6762-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6762-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="b6762-107">podczas</span><span class="sxs-lookup"><span data-stu-id="b6762-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6762-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6762-108">Remarks</span></span>  
 <span data-ttu-id="b6762-109">Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:</span><span class="sxs-lookup"><span data-stu-id="b6762-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="b6762-110">Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie powoduje wywołania zwrotnego debugera.</span><span class="sxs-lookup"><span data-stu-id="b6762-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="b6762-111">Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie powoduje wywołania zwrotnego debugera, jeśli wyjątek nigdy nie wyjdzie do kodu użytkownika (oznacza to, że ścieżka ze źródła wyjątku do procedury obsługi wyjątku nie ma metod oznaczonych jako JustMyCode lub JMC).</span><span class="sxs-lookup"><span data-stu-id="b6762-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="b6762-112">Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="b6762-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6762-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6762-113">Requirements</span></span>  
 <span data-ttu-id="b6762-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6762-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6762-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6762-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6762-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6762-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6762-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6762-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6762-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6762-118">See also</span></span>

- [<span data-ttu-id="b6762-119">ICorDebugProcess8, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6762-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="b6762-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6762-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
