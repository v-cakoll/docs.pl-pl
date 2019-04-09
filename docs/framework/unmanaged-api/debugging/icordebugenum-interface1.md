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
ms.openlocfilehash: 9afaeebfdb98a404ea53b0b5ec147f8c8104e14d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148814"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="08c20-102">ICorDebugEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="08c20-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="08c20-103">Służy jako abstrakcyjny interfejs podstawowy dla wyliczenia, które są używane przez aplikację do debugowania.</span><span class="sxs-lookup"><span data-stu-id="08c20-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08c20-104">Metody</span><span class="sxs-lookup"><span data-stu-id="08c20-104">Methods</span></span>  
  
|<span data-ttu-id="08c20-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="08c20-105">Method</span></span>|<span data-ttu-id="08c20-106">Opis</span><span class="sxs-lookup"><span data-stu-id="08c20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08c20-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="08c20-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="08c20-108">Tworzy kopię `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="08c20-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="08c20-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="08c20-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="08c20-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="08c20-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="08c20-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="08c20-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="08c20-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="08c20-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="08c20-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="08c20-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="08c20-114">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="08c20-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08c20-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08c20-115">Remarks</span></span>  
 <span data-ttu-id="08c20-116">Następujące moduły wyliczające pochodzić od `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="08c20-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="08c20-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="08c20-118">Icordebugassemblyenum "—"</span><span class="sxs-lookup"><span data-stu-id="08c20-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="08c20-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="08c20-120">Icordebugbreakpointenum "—"</span><span class="sxs-lookup"><span data-stu-id="08c20-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="08c20-121">Icordebugchainenum "—"</span><span class="sxs-lookup"><span data-stu-id="08c20-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="08c20-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="08c20-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="08c20-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="08c20-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="08c20-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="08c20-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="08c20-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="08c20-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="08c20-130">Icordebugmoduleenum "—"</span><span class="sxs-lookup"><span data-stu-id="08c20-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="08c20-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="08c20-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="08c20-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="08c20-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="08c20-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="08c20-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="08c20-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="08c20-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="08c20-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="08c20-138">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="08c20-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c20-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08c20-139">Requirements</span></span>  
 <span data-ttu-id="08c20-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c20-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c20-141">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08c20-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08c20-142">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08c20-142">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="08c20-143">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="08c20-143">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="08c20-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08c20-144">See also</span></span>

- [<span data-ttu-id="08c20-145">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="08c20-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
