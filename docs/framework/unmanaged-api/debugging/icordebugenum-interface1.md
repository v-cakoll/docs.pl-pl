---
title: ICorDebugEnum — Interfejs
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
ms.openlocfilehash: 59dcb7ae6f27f8d049cd4dc2d313f7f1130fc503
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085264"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="a0aa5-102">ICorDebugEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0aa5-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="a0aa5-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0aa5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a0aa5-104">Methods</span></span>  
  
|<span data-ttu-id="a0aa5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0aa5-105">Method</span></span>|<span data-ttu-id="a0aa5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a0aa5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0aa5-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="a0aa5-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="a0aa5-108">Tworzy kopię tego obiektu `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="a0aa5-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="a0aa5-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="a0aa5-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="a0aa5-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="a0aa5-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="a0aa5-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="a0aa5-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="a0aa5-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="a0aa5-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0aa5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0aa5-115">Remarks</span></span>  
 <span data-ttu-id="a0aa5-116">Następujące moduły wyliczające pochodzą z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="a0aa5-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="a0aa5-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="a0aa5-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="a0aa5-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="a0aa5-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="a0aa5-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="a0aa5-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="a0aa5-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="a0aa5-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="a0aa5-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="a0aa5-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="a0aa5-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="a0aa5-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="a0aa5-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="a0aa5-138">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a0aa5-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0aa5-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0aa5-139">Requirements</span></span>  
 <span data-ttu-id="a0aa5-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0aa5-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0aa5-141">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a0aa5-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0aa5-142">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a0aa5-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0aa5-143">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0aa5-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0aa5-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0aa5-144">See also</span></span>

- [<span data-ttu-id="a0aa5-145">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a0aa5-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
