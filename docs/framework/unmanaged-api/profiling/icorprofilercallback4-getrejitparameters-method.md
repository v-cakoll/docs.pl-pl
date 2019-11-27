---
title: ICorProfilerCallback4::GetReJITParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: d81d7275d197de1dfc99b135377459f509c2651f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439440"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="c405d-102">ICorProfilerCallback4::GetReJITParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="c405d-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="c405d-103">Umożliwia programowi Code Profiler Ustawianie alternatywnych flag generowania kodu dla nowej rekompilowanej treści metody.</span><span class="sxs-lookup"><span data-stu-id="c405d-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c405d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c405d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c405d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c405d-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c405d-106">podczas Moduł, który zawiera metodę, dla której środowisko CLR wymaga parametrów ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="c405d-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="c405d-107">podczas `MethodDef` metody, dla której środowisko CLR wymaga parametrów ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="c405d-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="c405d-108">podczas Wskaźnik do interfejsu [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) , który profiler może wykorzystać, aby dostarczyć informacje o ponownej kompilacji JIT dla metody, która jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="c405d-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c405d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c405d-109">Remarks</span></span>  
 <span data-ttu-id="c405d-110">Środowisko CLR generuje `GetReJITParameters` wywołanie zwrotne, dzięki czemu profiler może określić parametry ponownego kompilowania danej metody.</span><span class="sxs-lookup"><span data-stu-id="c405d-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="c405d-111">Wywołanie zwrotne `GetReJITParameters` jest wydawane tylko raz na funkcję; parametry dostarczone przez profiler stosują się do wszystkich wystąpień tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c405d-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c405d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c405d-112">Requirements</span></span>  
 <span data-ttu-id="c405d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c405d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c405d-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c405d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c405d-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c405d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c405d-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c405d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c405d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c405d-117">See also</span></span>

- [<span data-ttu-id="c405d-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c405d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c405d-119">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="c405d-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="c405d-120">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="c405d-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="c405d-121">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="c405d-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
