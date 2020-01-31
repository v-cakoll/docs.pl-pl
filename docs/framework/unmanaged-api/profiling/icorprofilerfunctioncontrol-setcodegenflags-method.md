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
ms.openlocfilehash: 75414ec3d2b30fe8afc5db1e97c81f34b29a3115
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864677"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="1a4b3-102">ICorProfilerFunctionControl::SetCodegenFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a4b3-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="1a4b3-103">Ustawia co najmniej jedną flagę z wyliczenia [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) , aby kontrolować generowanie kodu dla funkcji rekompilowanej just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="1a4b3-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a4b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a4b3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a4b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a4b3-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="1a4b3-106">podczas Co najmniej jedna flaga z wyliczenia [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1a4b3-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a4b3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a4b3-107">Remarks</span></span>  
 <span data-ttu-id="1a4b3-108">Profiler uzyskuje wystąpienie tego interfejsu za pomocą wywołania zwrotnego [ICorProfilerCallback4:: GetReJITParameters —](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a4b3-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="1a4b3-109">`SetCodegenFlags` pozwala profilerowi kontrolować generowanie kodu dla ponownie skompilowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="1a4b3-110">Podobnie jak w przypadku wszystkich innych parametrów ponownej kompilacji JIT, flagi generowania kodu stosują się do wszystkich wystąpień funkcji.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="1a4b3-111">Kompilator JIT traktuje te flagi kompilacji wraz z innymi flagami określonymi przez inne źródła podczas kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="1a4b3-112">Inne źródła obejmują debuger, flagi globalne ustawiane przez profiler przy uruchamianiu przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS`) i [ICorProfilerCallback:: JITInlining —](icorprofilercallback-jitinlining-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="1a4b3-113">Kompilator JIT daje pierwszeństwo dla źródła, które żąda najmniejszej ilości optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="1a4b3-114">Na przykład, jeśli Profiler określa `COR_PRF_DISABLE_INLINING` przy uruchamianiu, ale nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w wywołaniu zwrotnym [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) , nakreślenie jest nadal wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="1a4b3-115">Podobnie, jeśli Profiler nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags`, ale następnie wyłącza funkcję tworzenia konspektu przy użyciu wywołania zwrotnego [ICorProfilerCallback:: JITInlining —](icorprofilercallback-jitinlining-method.md) , wykreślanie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1a4b3-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a4b3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a4b3-116">Requirements</span></span>  
 <span data-ttu-id="1a4b3-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a4b3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a4b3-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1a4b3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a4b3-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a4b3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a4b3-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4b3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4b3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a4b3-121">See also</span></span>

- [<span data-ttu-id="1a4b3-122">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a4b3-122">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
