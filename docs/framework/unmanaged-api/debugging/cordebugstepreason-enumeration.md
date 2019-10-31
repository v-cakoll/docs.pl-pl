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
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133685"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="26b9b-102">CorDebugStepReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="26b9b-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="26b9b-103">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="26b9b-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26b9b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="26b9b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="26b9b-105">Members</span></span>  
  
|<span data-ttu-id="26b9b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="26b9b-106">Member</span></span>|<span data-ttu-id="26b9b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="26b9b-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="26b9b-108">Przechodzenie do normalnego działania w ramach tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="26b9b-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="26b9b-109">Dalsze dalsze przechodzenie po zwróceniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="26b9b-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="26b9b-110">Dalsze przechodzenie dalej na początku nowo wywołanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="26b9b-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="26b9b-111">Wygenerowano wyjątek i kontrola została przeniesiona do filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="26b9b-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="26b9b-112">Wygenerowano wyjątek i kontrola została przeniesiona do procedury obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="26b9b-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="26b9b-113">Kontrolka została przeniesiona do interceptora.</span><span class="sxs-lookup"><span data-stu-id="26b9b-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="26b9b-114">Wątek zakończył działanie przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="26b9b-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26b9b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26b9b-115">Requirements</span></span>  
 <span data-ttu-id="26b9b-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b9b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b9b-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26b9b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26b9b-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="26b9b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b9b-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b9b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b9b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26b9b-120">See also</span></span>

- [<span data-ttu-id="26b9b-121">StepComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="26b9b-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="26b9b-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="26b9b-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
