---
title: "CorDebugStepReason — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32892a14de820e8add38654cef92aa44930aec62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="64ee7-102">CorDebugStepReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="64ee7-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="64ee7-103">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="64ee7-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ee7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64ee7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="64ee7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="64ee7-105">Members</span></span>  
  
|<span data-ttu-id="64ee7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="64ee7-106">Member</span></span>|<span data-ttu-id="64ee7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="64ee7-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="64ee7-108">Wykonywanie krok po kroku zwykle zakończona w ramach tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="64ee7-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="64ee7-109">Wykonywanie krok po kroku nadal normalnie, po wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="64ee7-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="64ee7-110">Wykonywanie krok po kroku nadal normalnie na początku nowo wywołanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="64ee7-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="64ee7-111">Wyjątek został wygenerowany i formant został przekazany do filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="64ee7-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="64ee7-112">Wyjątek został wygenerowany i formant został przekazany do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="64ee7-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="64ee7-113">Formant został przekazany do interceptora.</span><span class="sxs-lookup"><span data-stu-id="64ee7-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="64ee7-114">Wątek został zakończony przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="64ee7-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64ee7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64ee7-115">Requirements</span></span>  
 <span data-ttu-id="64ee7-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64ee7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64ee7-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64ee7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64ee7-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64ee7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64ee7-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64ee7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ee7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64ee7-120">See Also</span></span>  
 [<span data-ttu-id="64ee7-121">StepComplete — metoda</span><span class="sxs-lookup"><span data-stu-id="64ee7-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="64ee7-122">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="64ee7-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
