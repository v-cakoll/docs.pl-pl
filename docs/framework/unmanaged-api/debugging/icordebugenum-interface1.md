---
title: ICorDebugEnum, interfejs1
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97080f7d850e67d635f9a65ee85ad3ddddbb244d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732755"
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="34ad6-102">ICorDebugEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="34ad6-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="34ad6-103">Służy jako abstrakcyjny interfejs podstawowy dla wyliczenia, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="34ad6-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34ad6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="34ad6-104">Methods</span></span>  
  
|<span data-ttu-id="34ad6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="34ad6-105">Method</span></span>|<span data-ttu-id="34ad6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="34ad6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34ad6-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="34ad6-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="34ad6-108">Tworzy kopię `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="34ad6-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="34ad6-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="34ad6-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="34ad6-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="34ad6-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="34ad6-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="34ad6-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="34ad6-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="34ad6-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="34ad6-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="34ad6-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="34ad6-114">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="34ad6-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34ad6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34ad6-115">Remarks</span></span>  
 <span data-ttu-id="34ad6-116">Następujące moduły wyliczające pochodzić od `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="34ad6-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="34ad6-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-118">Icordebugassemblyenum "—"</span><span class="sxs-lookup"><span data-stu-id="34ad6-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="34ad6-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="34ad6-120">Icordebugbreakpointenum "—"</span><span class="sxs-lookup"><span data-stu-id="34ad6-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-121">Icordebugchainenum "—"</span><span class="sxs-lookup"><span data-stu-id="34ad6-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="34ad6-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="34ad6-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="34ad6-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="34ad6-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="34ad6-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="34ad6-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="34ad6-130">Icordebugmoduleenum "—"</span><span class="sxs-lookup"><span data-stu-id="34ad6-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="34ad6-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="34ad6-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="34ad6-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="34ad6-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="34ad6-138">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="34ad6-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34ad6-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34ad6-139">Requirements</span></span>  
 <span data-ttu-id="34ad6-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34ad6-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34ad6-141">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34ad6-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34ad6-142">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34ad6-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34ad6-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34ad6-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ad6-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34ad6-144">See also</span></span>
- [<span data-ttu-id="34ad6-145">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="34ad6-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
