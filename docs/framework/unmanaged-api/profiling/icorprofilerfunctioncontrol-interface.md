---
title: ICorProfilerFunctionControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0daf772702ada9d426b3da6913fff0186e33564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="fe51d-102">ICorProfilerFunctionControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fe51d-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="fe51d-103">Udostępnia metody umożliwiające profilującego do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR), aby kontrolować sposób przy użyciu kompilatora JIT powinna generować kod ponowną kompilację określonej metody.</span><span class="sxs-lookup"><span data-stu-id="fe51d-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe51d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fe51d-104">Methods</span></span>  
  
|<span data-ttu-id="fe51d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe51d-105">Method</span></span>|<span data-ttu-id="fe51d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fe51d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe51d-107">SetCodegenFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="fe51d-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="fe51d-108">Określa jedną lub więcej flag z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) funkcja ponownie kompilowana wyliczenie do kontroli generowania kodu dla just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="fe51d-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="fe51d-109">SetILFunctionBody, metoda</span><span class="sxs-lookup"><span data-stu-id="fe51d-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="fe51d-110">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="fe51d-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="fe51d-111">SetILInstrumentedCodeMap, metoda</span><span class="sxs-lookup"><span data-stu-id="fe51d-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="fe51d-112">Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map wspólnego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="fe51d-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe51d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe51d-113">Remarks</span></span>  
 <span data-ttu-id="fe51d-114">`ICorProfilerFunctionControl` Interfejs zawiera metody służące do sterowania generowanie kodu dla jednej funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe51d-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="fe51d-115">Profiler uzyskuje wystąpienia tego interfejsu za pomocą [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fe51d-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="fe51d-116">Każde wystąpienie `ICorProfilerFunctionControl` steruje wszystkich wystąpień jednej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fe51d-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe51d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe51d-117">Requirements</span></span>  
 <span data-ttu-id="fe51d-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe51d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe51d-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe51d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe51d-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe51d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe51d-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe51d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe51d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe51d-122">See Also</span></span>  
 [<span data-ttu-id="fe51d-123">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe51d-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="fe51d-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="fe51d-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fe51d-125">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="fe51d-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
