---
title: CorDebugStepReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404534"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="c8262-102">CorDebugStepReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8262-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="c8262-103">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="c8262-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8262-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8262-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="c8262-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c8262-105">Members</span></span>  
  
|<span data-ttu-id="c8262-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c8262-106">Member</span></span>|<span data-ttu-id="c8262-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c8262-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="c8262-108">Wykonywanie krok po kroku zwykle zakończona w ramach tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c8262-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="c8262-109">Wykonywanie krok po kroku nadal normalnie, po wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="c8262-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="c8262-110">Wykonywanie krok po kroku nadal normalnie na początku nowo wywołanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c8262-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="c8262-111">Wyjątek został wygenerowany i formant został przekazany do filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c8262-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="c8262-112">Wyjątek został wygenerowany i formant został przekazany do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c8262-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="c8262-113">Formant został przekazany do interceptora.</span><span class="sxs-lookup"><span data-stu-id="c8262-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="c8262-114">Wątek został zakończony przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="c8262-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8262-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8262-115">Requirements</span></span>  
 <span data-ttu-id="c8262-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8262-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8262-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8262-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8262-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8262-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8262-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8262-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8262-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8262-120">See Also</span></span>  
 [<span data-ttu-id="c8262-121">StepComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="c8262-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="c8262-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8262-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
