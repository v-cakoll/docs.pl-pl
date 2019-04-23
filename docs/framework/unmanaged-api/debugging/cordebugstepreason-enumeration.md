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
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186254"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="90d33-102">CorDebugStepReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="90d33-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="90d33-103">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="90d33-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90d33-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="90d33-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="90d33-105">Members</span></span>  
  
|<span data-ttu-id="90d33-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="90d33-106">Member</span></span>|<span data-ttu-id="90d33-107">Opis</span><span class="sxs-lookup"><span data-stu-id="90d33-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="90d33-108">Przechodzenie krok po kroku zakończone normalnie w ramach tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="90d33-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="90d33-109">Przechodzenie krok po kroku nadal normalnie po wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="90d33-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="90d33-110">Na początku nowo wywołana funkcja przechodzenie krok po kroku nadal normalnie.</span><span class="sxs-lookup"><span data-stu-id="90d33-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="90d33-111">Wyjątek został wygenerowany i formant został przekazany do filtra wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90d33-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="90d33-112">Wyjątek został wygenerowany i formant został przekazany do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="90d33-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="90d33-113">Formant został przekazany do interceptor.</span><span class="sxs-lookup"><span data-stu-id="90d33-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="90d33-114">Wątek został zakończony przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="90d33-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90d33-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90d33-115">Requirements</span></span>  
 <span data-ttu-id="90d33-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90d33-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90d33-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90d33-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90d33-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90d33-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90d33-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90d33-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d33-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90d33-120">See also</span></span>

- [<span data-ttu-id="90d33-121">StepComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="90d33-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="90d33-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="90d33-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
