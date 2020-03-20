---
title: CorDebugInterfaceVersion — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: 5ebbbf01bc27974850c7e0bb3591b8f050fd0579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179274"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="9043c-102">CorDebugInterfaceVersion — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9043c-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="9043c-103">Określa interfejs, wersję programu .NET Framework lub wersję programu .NET Framework, w której wprowadzono interfejs.</span><span class="sxs-lookup"><span data-stu-id="9043c-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9043c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9043c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="9043c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9043c-105">Members</span></span>  
 <span data-ttu-id="9043c-106">Poniższa tabela zawiera łącza z każdej wartości wyliczenia do odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9043c-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="9043c-107">Ponadto tabela wskazuje pierwszą wersję programu .NET Framework, w których interfejs był obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="9043c-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="9043c-108">Członek</span><span class="sxs-lookup"><span data-stu-id="9043c-108">Member</span></span>|<span data-ttu-id="9043c-109">Określa</span><span class="sxs-lookup"><span data-stu-id="9043c-109">Specifies</span></span>|<span data-ttu-id="9043c-110">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9043c-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="9043c-111">Wersja programu .NET Framework jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="9043c-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="9043c-112">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 1.0.</span><span class="sxs-lookup"><span data-stu-id="9043c-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="9043c-113">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="9043c-114">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 1.1.</span><span class="sxs-lookup"><span data-stu-id="9043c-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="9043c-115">1.1</span><span class="sxs-lookup"><span data-stu-id="9043c-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="9043c-116">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 2.0.</span><span class="sxs-lookup"><span data-stu-id="9043c-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="9043c-117">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="9043c-118">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 4.</span><span class="sxs-lookup"><span data-stu-id="9043c-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="9043c-119">4</span><span class="sxs-lookup"><span data-stu-id="9043c-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="9043c-120">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 4.5.</span><span class="sxs-lookup"><span data-stu-id="9043c-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="9043c-121">4.5</span><span class="sxs-lookup"><span data-stu-id="9043c-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="9043c-122">ICorDebugManagedCallback (Powrót do łączenia)</span><span class="sxs-lookup"><span data-stu-id="9043c-122">ICorDebugManagedCallback</span></span>](icordebugmanagedcallback-interface.md)|<span data-ttu-id="9043c-123">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="9043c-124">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="9043c-124">ICorDebugUnmanagedCallback</span></span>](icordebugunmanagedcallback-interface.md)|<span data-ttu-id="9043c-125">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="9043c-126">Icordebug</span><span class="sxs-lookup"><span data-stu-id="9043c-126">ICorDebug</span></span>](icordebug-interface.md)|<span data-ttu-id="9043c-127">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="9043c-128">Kontroler ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9043c-128">ICorDebugController</span></span>](icordebugcontroller-interface.md)|<span data-ttu-id="9043c-129">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="9043c-130">Domena ICorDebugApp</span><span class="sxs-lookup"><span data-stu-id="9043c-130">ICorDebugAppDomain</span></span>](icordebugappdomain-interface.md)|<span data-ttu-id="9043c-131">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="9043c-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="9043c-132">ICorDebugAssembly</span></span>](icordebugassembly-interface.md)|<span data-ttu-id="9043c-133">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="9043c-134">Icordebugprocess</span><span class="sxs-lookup"><span data-stu-id="9043c-134">ICorDebugProcess</span></span>](icordebugprocess-interface.md)|<span data-ttu-id="9043c-135">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="9043c-136">Icordebugbreakpoint</span><span class="sxs-lookup"><span data-stu-id="9043c-136">ICorDebugBreakpoint</span></span>](icordebugbreakpoint-interface.md)|<span data-ttu-id="9043c-137">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="9043c-138">ICorDebugFunctionBreakpoint (Punkt przerwania)</span><span class="sxs-lookup"><span data-stu-id="9043c-138">ICorDebugFunctionBreakpoint</span></span>](icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="9043c-139">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="9043c-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9043c-140">ICorDebugModuleBreakpoint</span></span>](icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="9043c-141">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="9043c-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9043c-142">ICorDebugValueBreakpoint</span></span>](icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="9043c-143">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="9043c-144">ICorDebugStepper (ICorDebugStepper)</span><span class="sxs-lookup"><span data-stu-id="9043c-144">ICorDebugStepper</span></span>](icordebugstepper-interface.md)|<span data-ttu-id="9043c-145">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="9043c-146">Zestaw rejestrów ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9043c-146">ICorDebugRegisterSet</span></span>](icordebugregisterset-interface.md)|<span data-ttu-id="9043c-147">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="9043c-148">Icordebugthread</span><span class="sxs-lookup"><span data-stu-id="9043c-148">ICorDebugThread</span></span>](icordebugthread-interface.md)|<span data-ttu-id="9043c-149">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="9043c-150">ICorDebugChain (ICorDebugChain)</span><span class="sxs-lookup"><span data-stu-id="9043c-150">ICorDebugChain</span></span>](icordebugchain-interface.md)|<span data-ttu-id="9043c-151">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="9043c-152">Icordebugframe</span><span class="sxs-lookup"><span data-stu-id="9043c-152">ICorDebugFrame</span></span>](icordebugframe-interface.md)|<span data-ttu-id="9043c-153">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="9043c-154">Ramka ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="9043c-154">ICorDebugILFrame</span></span>](icordebugilframe-interface.md)|<span data-ttu-id="9043c-155">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="9043c-156">Ramka ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="9043c-156">ICorDebugNativeFrame</span></span>](icordebugnativeframe-interface.md)|<span data-ttu-id="9043c-157">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="9043c-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="9043c-158">ICorDebugModule</span></span>](icordebugmodule-interface.md)|<span data-ttu-id="9043c-159">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="9043c-160">Icordebugfunction</span><span class="sxs-lookup"><span data-stu-id="9043c-160">ICorDebugFunction</span></span>](icordebugfunction-interface1.md)|<span data-ttu-id="9043c-161">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="9043c-162">Icordebugcode</span><span class="sxs-lookup"><span data-stu-id="9043c-162">ICorDebugCode</span></span>](icordebugcode-interface1.md)|<span data-ttu-id="9043c-163">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="9043c-164">Icordebugclass</span><span class="sxs-lookup"><span data-stu-id="9043c-164">ICorDebugClass</span></span>](icordebugclass-interface.md)|<span data-ttu-id="9043c-165">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="9043c-166">ICorDebugZawal</span><span class="sxs-lookup"><span data-stu-id="9043c-166">ICorDebugEval</span></span>](icordebugeval-interface.md)|<span data-ttu-id="9043c-167">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="9043c-168">Icordebugvalue</span><span class="sxs-lookup"><span data-stu-id="9043c-168">ICorDebugValue</span></span>](icordebugvalue-interface.md)|<span data-ttu-id="9043c-169">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="9043c-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="9043c-170">ICorDebugGenericValue</span></span>](icordebuggenericvalue-interface.md)|<span data-ttu-id="9043c-171">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="9043c-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="9043c-172">ICorDebugReferenceValue</span></span>](icordebugreferencevalue-interface.md)|<span data-ttu-id="9043c-173">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="9043c-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="9043c-174">ICorDebugHeapValue</span></span>](icordebugheapvalue-interface.md)|<span data-ttu-id="9043c-175">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="9043c-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="9043c-176">ICorDebugObjectValue</span></span>](icordebugobjectvalue-interface.md)|<span data-ttu-id="9043c-177">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="9043c-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="9043c-178">ICorDebugBoxValue</span></span>](icordebugboxvalue-interface.md)|<span data-ttu-id="9043c-179">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="9043c-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="9043c-180">ICorDebugStringValue</span></span>](icordebugstringvalue-interface.md)|<span data-ttu-id="9043c-181">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="9043c-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="9043c-182">ICorDebugArrayValue</span></span>](icordebugarrayvalue-interface.md)|<span data-ttu-id="9043c-183">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="9043c-184">ICorDebugKontekst</span><span class="sxs-lookup"><span data-stu-id="9043c-184">ICorDebugContext</span></span>](icordebugcontext-interface.md)|<span data-ttu-id="9043c-185">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="9043c-186">Icordebugenum</span><span class="sxs-lookup"><span data-stu-id="9043c-186">ICorDebugEnum</span></span>](icordebugenum-interface1.md)|<span data-ttu-id="9043c-187">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="9043c-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-188">ICorDebugObjectEnum</span></span>](icordebugobjectenum-interface.md)|<span data-ttu-id="9043c-189">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="9043c-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-190">ICorDebugBreakpointEnum</span></span>](icordebugbreakpointenum-interface.md)|<span data-ttu-id="9043c-191">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="9043c-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-192">ICorDebugStepperEnum</span></span>](icordebugstepperenum-interface.md)|<span data-ttu-id="9043c-193">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="9043c-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-194">ICorDebugProcessEnum</span></span>](icordebugprocessenum-interface.md)|<span data-ttu-id="9043c-195">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="9043c-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-196">ICorDebugThreadEnum</span></span>](icordebugthreadenum-interface1.md)|<span data-ttu-id="9043c-197">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="9043c-198">ICorDebugFrameEnum ( ICorDebugFrameEnum )</span><span class="sxs-lookup"><span data-stu-id="9043c-198">ICorDebugFrameEnum</span></span>](icordebugframeenum-interface.md)|<span data-ttu-id="9043c-199">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="9043c-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-200">ICorDebugChainEnum</span></span>](icordebugchainenum-interface.md)|<span data-ttu-id="9043c-201">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="9043c-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-202">ICorDebugModuleEnum</span></span>](icordebugmoduleenum-interface.md)|<span data-ttu-id="9043c-203">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="9043c-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-204">ICorDebugValueEnum</span></span>](icordebugvalueenum-interface.md)|<span data-ttu-id="9043c-205">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="9043c-206">Kod ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9043c-206">ICorDebugCodeEnum</span></span>](icordebugcodeenum-interface.md)|<span data-ttu-id="9043c-207">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="9043c-208">ICorDebugTypeEnum ( ICorDebugTypeEnum )</span><span class="sxs-lookup"><span data-stu-id="9043c-208">ICorDebugTypeEnum</span></span>](icordebugtypeenum-interface.md)|<span data-ttu-id="9043c-209">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="9043c-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-210">ICorDebugErrorInfoEnum</span></span>](icordebugerrorinfoenum-interface.md)|<span data-ttu-id="9043c-211">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="9043c-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-212">ICorDebugAppDomainEnum</span></span>](icordebugappdomainenum-interface.md)|<span data-ttu-id="9043c-213">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="9043c-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="9043c-214">ICorDebugAssemblyEnum</span></span>](icordebugassemblyenum-interface.md)|<span data-ttu-id="9043c-215">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="9043c-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="9043c-216">ICorDebugEditAndContinueErrorInfo</span></span>](icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="9043c-217">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="9043c-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="9043c-218">ICorDebugEditAndContinueSnapshot</span></span>](icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="9043c-219">1.0</span><span class="sxs-lookup"><span data-stu-id="9043c-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="9043c-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="9043c-220">ICorDebugManagedCallback2</span></span>](icordebugmanagedcallback2-interface.md)|<span data-ttu-id="9043c-221">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="9043c-222">Domena ICorDebugApp2</span><span class="sxs-lookup"><span data-stu-id="9043c-222">ICorDebugAppDomain2</span></span>](icordebugappdomain2-interface.md)|<span data-ttu-id="9043c-223">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="9043c-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="9043c-224">ICorDebugProcess2</span></span>](icordebugprocess2-interface1.md)|<span data-ttu-id="9043c-225">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="9043c-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="9043c-226">ICorDebugStepper2</span></span>](icordebugstepper2-interface1.md)|<span data-ttu-id="9043c-227">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="9043c-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="9043c-228">ICorDebugRegisterSet2</span></span>](icordebugregisterset2-interface.md)|<span data-ttu-id="9043c-229">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="9043c-230">ICorDebugNastawa2</span><span class="sxs-lookup"><span data-stu-id="9043c-230">ICorDebugThread2</span></span>](icordebugthread2-interface.md)|<span data-ttu-id="9043c-231">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="9043c-232">Klatka ICorDebugIL2</span><span class="sxs-lookup"><span data-stu-id="9043c-232">ICorDebugILFrame2</span></span>](icordebugilframe2-interface.md)|<span data-ttu-id="9043c-233">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="9043c-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="9043c-234">ICorDebugModule2</span></span>](icordebugmodule2-interface.md)|<span data-ttu-id="9043c-235">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="9043c-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="9043c-236">ICorDebugFunction2</span></span>](icordebugfunction2-interface.md)|<span data-ttu-id="9043c-237">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="9043c-238">Kod ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="9043c-238">ICorDebugCode2</span></span>](icordebugcode2-interface.md)|<span data-ttu-id="9043c-239">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="9043c-240">"ICorDebugClass2"</span><span class="sxs-lookup"><span data-stu-id="9043c-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="9043c-241">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="9043c-242">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="9043c-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="9043c-243">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="9043c-244">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="9043c-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="9043c-245">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="9043c-246">"ICorDebugObjectValue2"</span><span class="sxs-lookup"><span data-stu-id="9043c-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="9043c-247">2.0</span><span class="sxs-lookup"><span data-stu-id="9043c-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="9043c-248">ICorDebugNastawa3</span><span class="sxs-lookup"><span data-stu-id="9043c-248">ICorDebugThread3</span></span>](icordebugthread3-interface.md)|<span data-ttu-id="9043c-249">4</span><span class="sxs-lookup"><span data-stu-id="9043c-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="9043c-250">ICorDebugNajuż</span><span class="sxs-lookup"><span data-stu-id="9043c-250">ICorDebugThread4</span></span>](icordebugthread4-interface.md)|<span data-ttu-id="9043c-251">4</span><span class="sxs-lookup"><span data-stu-id="9043c-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="9043c-252">Icordebugstackwalk</span><span class="sxs-lookup"><span data-stu-id="9043c-252">ICorDebugStackWalk</span></span>](icordebugstackwalk-interface.md)|<span data-ttu-id="9043c-253">4</span><span class="sxs-lookup"><span data-stu-id="9043c-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="9043c-254">Ramka ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="9043c-254">ICorDebugNativeFrame2</span></span>](icordebugnativeframe2-interface.md)|<span data-ttu-id="9043c-255">4</span><span class="sxs-lookup"><span data-stu-id="9043c-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="9043c-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="9043c-256">ICorDebugInternalFrame2</span></span>](icordebuginternalframe2-interface.md)|<span data-ttu-id="9043c-257">4</span><span class="sxs-lookup"><span data-stu-id="9043c-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="9043c-258">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="9043c-258">ICorDebugRuntimeUnwindableFrame</span></span>](icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="9043c-259">4</span><span class="sxs-lookup"><span data-stu-id="9043c-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="9043c-260">ICorDebugHeapValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9043c-260">ICorDebugHeapValue3 Interface</span></span>](icordebugheapvalue3-interface.md)|<span data-ttu-id="9043c-261">4</span><span class="sxs-lookup"><span data-stu-id="9043c-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="9043c-262">ICorDebugBlockingObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9043c-262">ICorDebugBlockingObjectEnum Interface</span></span>](icordebugblockingobjectenum-interface.md)|<span data-ttu-id="9043c-263">4</span><span class="sxs-lookup"><span data-stu-id="9043c-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="9043c-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="9043c-264">ICorDebugValue3</span></span>](icordebugvalue3-interface.md)|<span data-ttu-id="9043c-265">4</span><span class="sxs-lookup"><span data-stu-id="9043c-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="9043c-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="9043c-266">ICorDebugComObjectValue</span></span>](icordebugcomobjectvalue-interface.md)|<span data-ttu-id="9043c-267">4.5</span><span class="sxs-lookup"><span data-stu-id="9043c-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="9043c-268">Domena ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="9043c-268">ICorDebugAppDomain3</span></span>](icordebugappdomain3-interface.md)|<span data-ttu-id="9043c-269">4.5</span><span class="sxs-lookup"><span data-stu-id="9043c-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="9043c-270">Kod ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="9043c-270">ICorDebugCode3</span></span>](icordebugcode3-interface.md)|<span data-ttu-id="9043c-271">4.5</span><span class="sxs-lookup"><span data-stu-id="9043c-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="9043c-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="9043c-272">ICorDebugILFrame3</span></span>](icordebugilframe3-interface.md)|<span data-ttu-id="9043c-273">4.5</span><span class="sxs-lookup"><span data-stu-id="9043c-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="9043c-274">Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest najnowszą wersją.</span><span class="sxs-lookup"><span data-stu-id="9043c-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="9043c-275">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9043c-275">Remarks</span></span>  
 <span data-ttu-id="9043c-276">Debuger może użyć `CorDebugInterfaceVersion` wyliczenia w [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, aby określić najwyższą wersję .NET Framework, który obsługuje debuger.</span><span class="sxs-lookup"><span data-stu-id="9043c-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="9043c-277">Nazwy interfejsów</span><span class="sxs-lookup"><span data-stu-id="9043c-277">Interface Names</span></span>  
 <span data-ttu-id="9043c-278">Numer, który pojawia się na końcu nazw interfejsu w debugowaniu interfejsu API `ICorDebugThread3`(na przykład "3" w ) określa wersję interfejsu, a nie wersję .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9043c-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="9043c-279">Wszystkie nazwy interfejsów w debugowaniu interfejsu API zawierają numery wersji z wyjątkiem interfejsów, które zostały wprowadzone w wersji .NET Framework w wersji 1.</span><span class="sxs-lookup"><span data-stu-id="9043c-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="9043c-280">Wszelka korespondencja między numerami wersji interfejsu and.NET numerami wersji Framework są przypadkowe.</span><span class="sxs-lookup"><span data-stu-id="9043c-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="9043c-281">Interfejsy, które zostały wprowadzone w .NET Framework w wersji 1.0 nie zawierają liczby, ponieważ wszystkie są one niejawnie w wersji 1.</span><span class="sxs-lookup"><span data-stu-id="9043c-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="9043c-282">Program .NET Framework w wersji 1.1 używa interfejsów w wersji 1.0 i nie wprowadza żadnych nowych interfejsów debugowania.</span><span class="sxs-lookup"><span data-stu-id="9043c-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="9043c-283">14 interfejsów debugowania wprowadzonych w wersji .NET Framework 2.0 są logicznymi rozszerzeniami ich odpowiedników w wersji 1 i zawierają liczbę "2" w ich nazwach.</span><span class="sxs-lookup"><span data-stu-id="9043c-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="9043c-284">Program .NET Framework w wersjach 3.0 i 3.5 korzysta z istniejących interfejsów .NET Framework 2.0 i nie wprowadza żadnych nowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9043c-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="9043c-285">.NET Framework 4 wprowadza kombinację wersji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9043c-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="9043c-286">Na przykład `ICorDebugThread3` zarówno `ICorDebugThread4` i pojawiają się jako `ICorDebugThread` trzecia i czwarta wersja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9043c-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="9043c-287">.NET Framework 4 wprowadza również pierwszą `ICorDebugStackWalk` wersję interfejsu i `ICorDebugNativeFrame` drugą`ICorDebugNativeFrame2`wersję interfejsu ( ).</span><span class="sxs-lookup"><span data-stu-id="9043c-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9043c-288">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9043c-288">Requirements</span></span>  
 <span data-ttu-id="9043c-289">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9043c-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9043c-290">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9043c-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9043c-291">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9043c-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9043c-292">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9043c-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9043c-293">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9043c-293">See also</span></span>

- [<span data-ttu-id="9043c-294">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9043c-294">Debugging Enumerations</span></span>](debugging-enumerations.md)
