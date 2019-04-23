---
title: ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d04c15fa181d0e7bf8a92c1b6ecdef5b8b13bd7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182432"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="43712-102">ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="43712-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="43712-103">Określa funkcję implementowany przez program profilujący zostanie wywołana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do programu profilującego funkcji punktów zaczepienia wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="43712-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="43712-104">Ta metoda jest rozszerzeniem [icorprofilerinfo::setfunctionidmapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metody z parametrem dodatkowe dane profilowania może używać w celu rozróżniać wśród modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="43712-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43712-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="43712-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43712-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="43712-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="43712-107">[in] Wskaźnik do [functionidmapper2 —](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementację, która zostanie wywołana w celu mapowania `FunctionID` wartości w celu ich alternatywne wartości.</span><span class="sxs-lookup"><span data-stu-id="43712-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="43712-108">[in] Wskaźnik, który jest przekazywany do każdej [functionidmapper2 —](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) wywołania funkcji przez bieżącego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="43712-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="43712-109">Profiler można użyć tych informacji aby rozróżniać wśród modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="43712-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43712-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="43712-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43712-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43712-111">Remarks</span></span>  
 <span data-ttu-id="43712-112">Alternatywy dla wartości FunctionID zostaną przekazane do programu profilującego funkcja wejścia/wyjścia w punkty zaczepienia ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; lub [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) które są określone przez [ Setenterleavefunctionhooks3 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) lub [setenterleavefunctionhooks3withinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="43712-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="43712-113">`FunctionIDMapper2` Metody można ustawić tylko raz; zalecamy ustawienie [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="43712-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43712-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43712-114">Requirements</span></span>  
 <span data-ttu-id="43712-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43712-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43712-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43712-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43712-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43712-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43712-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43712-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43712-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43712-119">See also</span></span>

- [<span data-ttu-id="43712-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="43712-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="43712-121">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="43712-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="43712-122">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="43712-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="43712-123">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="43712-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
