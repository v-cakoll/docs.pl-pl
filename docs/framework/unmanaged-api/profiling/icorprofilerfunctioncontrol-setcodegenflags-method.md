---
title: "ICorProfilerFunctionControl::SetCodegenFlags — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetCodegenFlags
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9264e717da62c88b6f2f6eca262b5635fc928741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="34515-102">ICorProfilerFunctionControl::SetCodegenFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="34515-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="34515-103">Określa jedną lub więcej flag z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) funkcja ponownie kompilowana wyliczenie do kontroli generowania kodu dla just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="34515-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34515-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34515-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34515-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34515-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="34515-106">[in] Jeden lub więcej flag z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="34515-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34515-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34515-107">Remarks</span></span>  
 <span data-ttu-id="34515-108">Profiler uzyskuje wystąpienia tego interfejsu za pomocą [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="34515-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="34515-109">`SetCodegenFlags`Umożliwia profiler do kontrolowania generowanie kodu dla funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="34515-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="34515-110">Podobnie jak w przypadku wszystkich innych JIT kompilację parametrów, flagi generowania kodu mają zastosowanie do wszystkich wystąpień funkcji.</span><span class="sxs-lookup"><span data-stu-id="34515-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="34515-111">Kompilator JIT uwzględnia te flagi kompilowania, wraz z innymi flag określonych przez inne źródła, podczas kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="34515-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="34515-112">Inne źródła obejmują debugera, flagi globalne ustawione przez profiler przy uruchamianiu przez przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) — metoda (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS`) i profilera [ ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="34515-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="34515-113">Kompilator JIT daje pierwszeństwo źródłem żądań najmniejszą liczbą optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="34515-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="34515-114">Na przykład, jeśli określa profilera `COR_PRF_DISABLE_INLINING` podczas uruchamiania, ale nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) wywołania zwrotnego ze śródwierszowaniem nadal jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="34515-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="34515-115">Podobnie jeśli profilera nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags`, ale następnie wyłącza ze śródwierszowaniem przy użyciu [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotnego ze śródwierszowaniem jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="34515-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34515-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34515-116">Requirements</span></span>  
 <span data-ttu-id="34515-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34515-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34515-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34515-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34515-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34515-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34515-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34515-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34515-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34515-121">See Also</span></span>  
 [<span data-ttu-id="34515-122">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="34515-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
