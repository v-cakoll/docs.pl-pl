---
title: ICorDebugEnum, interfejs
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
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976333"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="8c233-102">ICorDebugEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c233-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="8c233-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="8c233-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c233-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c233-104">Methods</span></span>  
  
|<span data-ttu-id="8c233-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c233-105">Method</span></span>|<span data-ttu-id="8c233-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8c233-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c233-107">Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c233-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="8c233-108">Tworzy kopię tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c233-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="8c233-109">GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c233-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="8c233-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="8c233-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="8c233-111">Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c233-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="8c233-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8c233-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="8c233-113">Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c233-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="8c233-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="8c233-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c233-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c233-115">Remarks</span></span>  
 <span data-ttu-id="8c233-116">Następujące moduły wyliczające pochodzą z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="8c233-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="8c233-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="8c233-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="8c233-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="8c233-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="8c233-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="8c233-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="8c233-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="8c233-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="8c233-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="8c233-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="8c233-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="8c233-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="8c233-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="8c233-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="8c233-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="8c233-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="8c233-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="8c233-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="8c233-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="8c233-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="8c233-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="8c233-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="8c233-138">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="8c233-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c233-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c233-139">Requirements</span></span>  
 <span data-ttu-id="8c233-140">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c233-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c233-141">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c233-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c233-142">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c233-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c233-143">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c233-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c233-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c233-144">See also</span></span>

- [<span data-ttu-id="8c233-145">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c233-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
