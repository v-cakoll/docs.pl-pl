---
title: ICorDebugEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum
helpviewer_keywords: ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751cca87962473501ef29a4deb99d9d24be33396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="341ea-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="341ea-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="341ea-103">Pełni rolę abstrakcyjnej interfejs podstawowy dla wyliczenia, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="341ea-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="341ea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="341ea-104">Methods</span></span>  
  
|<span data-ttu-id="341ea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="341ea-105">Method</span></span>|<span data-ttu-id="341ea-106">Opis</span><span class="sxs-lookup"><span data-stu-id="341ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="341ea-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="341ea-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="341ea-108">Tworzy kopię tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="341ea-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="341ea-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="341ea-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="341ea-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="341ea-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="341ea-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="341ea-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="341ea-112">Przesuwa kursor na początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="341ea-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="341ea-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="341ea-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="341ea-114">Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="341ea-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="341ea-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="341ea-115">Remarks</span></span>  
 <span data-ttu-id="341ea-116">Następujące moduły wyliczające pochodzi od `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="341ea-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="341ea-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="341ea-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="341ea-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="341ea-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="341ea-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="341ea-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="341ea-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="341ea-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="341ea-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="341ea-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="341ea-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="341ea-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="341ea-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="341ea-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="341ea-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="341ea-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="341ea-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="341ea-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="341ea-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="341ea-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="341ea-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="341ea-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="341ea-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="341ea-138">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="341ea-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="341ea-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="341ea-139">Requirements</span></span>  
 <span data-ttu-id="341ea-140">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="341ea-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="341ea-141">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="341ea-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="341ea-142">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="341ea-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="341ea-143">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="341ea-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341ea-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="341ea-144">See Also</span></span>  
 [<span data-ttu-id="341ea-145">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="341ea-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
