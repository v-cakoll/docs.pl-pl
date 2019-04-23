---
title: ICorProfilerFunctionControl::SetCodegenFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104445"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="3bed1-102">ICorProfilerFunctionControl::SetCodegenFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bed1-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="3bed1-103">Ustawia flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia do sterowania generowanie kodu dla just-in-time (JIT) ponownie kompilowana funkcji.</span><span class="sxs-lookup"><span data-stu-id="3bed1-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bed1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bed1-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bed1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bed1-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="3bed1-106">[in] Flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3bed1-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bed1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bed1-107">Remarks</span></span>  
 <span data-ttu-id="3bed1-108">Program profilujący uzyskuje wystąpienie ten interfejs, za pośrednictwem [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3bed1-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="3bed1-109">`SetCodegenFlags` Umożliwia profiler kontrolować generowanie kodu dla funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3bed1-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="3bed1-110">Podobnie jak w przypadku wszystkich innych JIT ponownej kompilacji parametrów flagi generowania kodu mają zastosowanie do wszystkich wystąpień funkcji.</span><span class="sxs-lookup"><span data-stu-id="3bed1-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="3bed1-111">Kompilator JIT uwzględnia te flagi kompilacji oraz inne flagi, określony przez inne źródła, podczas kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="3bed1-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="3bed1-112">Inne źródła dołączyć debuger, flagi globalnej ustawione przez profiler przy uruchamianiu przez przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) — metoda (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS`) i programu profilującego [ Icorprofilercallback::jitinlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3bed1-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="3bed1-113">Kompilator JIT daje pierwszeństwo źródła, który żąda najmniejszą ilością optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="3bed1-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="3bed1-114">Na przykład, jeśli program profilujący Określa `COR_PRF_DISABLE_INLINING` podczas uruchamiania, ale nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) wywołanie zwrotne, wbudowanie nadal jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3bed1-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="3bed1-115">Podobnie jeśli program profilujący nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags`, ale następnie wyłącza wbudowanie przy użyciu [icorprofilercallback::jitinlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołanie zwrotne, wbudowanie jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3bed1-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bed1-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bed1-116">Requirements</span></span>  
 <span data-ttu-id="3bed1-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bed1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bed1-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bed1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bed1-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bed1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bed1-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bed1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bed1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bed1-121">See also</span></span>

- [<span data-ttu-id="3bed1-122">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bed1-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
