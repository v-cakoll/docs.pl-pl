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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25c47e101ad0fb8e8cbdbb2718a41c9be6c0c22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931982"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="a7ac4-102">ICorDebugEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ac4-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="a7ac4-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7ac4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a7ac4-104">Methods</span></span>  
  
|<span data-ttu-id="a7ac4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a7ac4-105">Method</span></span>|<span data-ttu-id="a7ac4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a7ac4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7ac4-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="a7ac4-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="a7ac4-108">Tworzy kopię tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="a7ac4-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="a7ac4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="a7ac4-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="a7ac4-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="a7ac4-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="a7ac4-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="a7ac4-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="a7ac4-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="a7ac4-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ac4-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7ac4-115">Remarks</span></span>  
 <span data-ttu-id="a7ac4-116">Następujące moduły wyliczające pochodzą z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="a7ac4-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="a7ac4-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="a7ac4-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="a7ac4-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="a7ac4-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="a7ac4-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="a7ac4-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="a7ac4-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="a7ac4-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="a7ac4-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="a7ac4-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="a7ac4-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="a7ac4-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="a7ac4-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="a7ac4-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="a7ac4-138">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a7ac4-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ac4-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7ac4-139">Requirements</span></span>  
 <span data-ttu-id="a7ac4-140">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ac4-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ac4-141">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ac4-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ac4-142">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ac4-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ac4-143">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ac4-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ac4-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7ac4-144">See also</span></span>

- [<span data-ttu-id="a7ac4-145">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7ac4-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
